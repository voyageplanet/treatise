# 记一枚 USB 无线网卡

&emsp;&emsp;这是一例失败的采购，有必要将它失败的过程记录下来。好，这货的名字叫「TP-LINK TL-WN725N 3.0 (免驱版) 181022」，购于万能的某宝。最初的目的是用在虚拟机 Kali 里面，做无线安全审计。其实当初如果用「Kali Linux 无线网卡」做关键字搜索，就能搜到在 Linux 上免驱的无线网卡，可惜我没有。它长这个样子，上面也有「免驱」字样，不过是在 Windows 平台免驱。将它插入笔记本电脑，Windows 10 将它认成一个 U 盘，里面有 EXE 文件，还是要双击安装驱动，所谓的「免驱」不过如此。

&emsp;&emsp;![Kali wlan0](https://github.com/voyageplanet/plan42/blob/master/99_file/01_img/20181127-kali-wlan0-03.png)

&emsp;&emsp;按照网上的教程，先配置 Virtual Box 里的 USB 设备和网络连接方式，启动 Kali 之后，用 lsusb 命令能够看到 USB 设备，号码是「0bda:b711」。

&emsp;&emsp;![Kali wlan0](https://github.com/voyageplanet/plan42/blob/master/99_file/01_img/20181127-kali-wlan0-02.png)

&emsp;&emsp;通过查询，设备「0bda:b711」使用 Realtek 的芯片，代号「RTL8188GU」。

&emsp;&emsp;![Kali wlan0](https://github.com/voyageplanet/plan42/blob/master/99_file/01_img/20181127-kali-wlan0-01.png)

&emsp;&emsp;关于该芯片如何安装 Linux 驱动的信息极其有限，更不用说比较冷门的 Kali。这时用 TL-WN725N 关键字搜索，看到好几篇文章介绍如何安装，但奇怪的是，作者的无线网卡却使用 RTL8188EU 芯片。管它呢，先试试在说。结果出错了。

&emsp;&emsp;![Kali wlan0](https://github.com/voyageplanet/plan42/blob/master/99_file/01_img/20181127-kali-wlan0-04.png)

&emsp;&emsp;再去 git 一个源码，编译，无用。

&emsp;&emsp;![Kali wlan0](https://github.com/voyageplanet/plan42/blob/master/99_file/01_img/20181127-kali-wlan0-08.png)

&emsp;&emsp;看到一篇国外的文章，说是要跑 usb_modeswitch 命令。跑一遍，出错。

&emsp;&emsp;![Kali wlan0](https://github.com/voyageplanet/plan42/blob/master/99_file/01_img/20181127-kali-wlan0-05.png)

&emsp;&emsp;干脆去 TP-LINK 官网，果然在英文官网上找到 TL-WN725N 3.0 的驱动下载页面，居然还有 Linux 驱动下载！大喜，下载，解压，编译，出错。出错信息如天书，根本看不懂。

&emsp;&emsp;![Kali wlan0](https://github.com/voyageplanet/plan42/blob/master/99_file/01_img/20181127-kali-wlan0-06.png)

&emsp;&emsp;进入 bin 目录，强行跑 insmod 命令，还是出错。

&emsp;&emsp;![Kali wlan0](https://github.com/voyageplanet/plan42/blob/master/99_file/01_img/20181127-kali-wlan0-07.png)

&emsp;&emsp;不死心，关掉 Kali，启动 Ubuntu，重新再来一遍。失败。最终决定将此无线网卡束之高阁。

&emsp;&emsp;

&emsp;&emsp;※ 沈翎，二〇一八年十一月廿七日 ※