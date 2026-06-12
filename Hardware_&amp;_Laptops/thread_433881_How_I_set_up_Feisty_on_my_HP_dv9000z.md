---
title: "How I set up Feisty on my HP dv9000z"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by rfrey74 on 2007-05-05
I decided to chronicle my experience of setting up Feisty on the notorious HP dv9000z laptop in the hope that others may find it useful.  So without further ado, here is the process I used to setup Feisty on my HP dv9000z

Setting up Feisty on HP dv9000z Laptop

Hardware Profile

$ cat /proc/cpuinfo

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 76
model name	: Mobile AMD Sempron(tm) Processor 3500+
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cr8legacy ts fid vid ttp tm stc
bogomips	: 1608.81
clflush size	: 64

$ lspci

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

Partitioning

/dev/sda1	30 GB	NTFS	C:\
/dev/sda2	10 GB	EXT3	/
/dev/sda3	58 GB	XFS	/home
/dev/sda4	2 GB	SWAP	swap

Post Installation Setup

$ sudo apt-get update
$ sudo apt-get dist-upgrade
$ sudo apt-get install sun-java6-jdk

Drivers

$ sudo gedit /etc/modprobe.d/blacklist
Type the following at the end of the file
# default wireless ethernet driver
blacklist bcm43xx
Save and close gedit
$ sudo modprobe -r bcm43xx
$ sudo apt-get install ndiswrapper-utils-1.9
Required Windows drivers are bcmwl5.inf and bcmwl5.sys from installer sp34152A.exe
Unplug ethernet cable
$ sudo ndiswrapper -i bcmwl5.inf
$ sudo ndiswrapper -m
$ sudo gedit /etc/modprobe.d/ndiswrapper
Replace wlan0 with eth1
Save and close gedit
$ sudo gedit /etc/network/if-pre-up.d/wireless-tools
Find the following block of code
if [ -n "$IF_WIRELESS_ESSID" ]; then
  $IWCONFIG "$IFACE" essid "$IF_WIRELESS_ESSID"
fi
and edit it as follows.
if [ -n "$IF_WIRELESS_ESSID" ]; then
  $IWCONFIG "$IFACE" essid "$IF_WIRELESS_ESSID"
else 
  $IWCONFIG "$IFACE" essid any
fi
Save and close gedit
$ sudo ifup -a
Use the network manager applet to connect to a wireless network.
$ sudo restricited-manager
Check the "Enabled" box next to NVIDIA accelerated graphics driver.
The restricted deiver manager will automatically install nvidia-glx and configure xorg.conf.
Unfortunately, nvidia-glx is the wrong driver.  Before rebooting install the correct driver.
$ sudo apt-get install nvidia-glx-new
$ sudo reboot

Multimedia

$ sudo gedit /etc/apt/sources.list
Add the following to the end of the file
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 
Save and close gedit
$ sudo wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install msttcorefonts flashplugin-nonfree
$ sudo apt-get install totem-xine libxine-extracodecs
$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
$ sudo apt-get install w32codecs libdvdcss2

---

### Post by kmh27 on 2007-05-16
Thanks for the post, looks helpful.

Wondering how you like your overall experience with this machine running feisty.  Considering buying one of these.

Most hardware recognized?
 bluetooth?
 webcam/mic?
 memory card readers?

---

### Post by rfrey74 on 2007-05-21
Actually, I bought this laptop with the express purpose to run Ubuntu on it.  However, Dapper did not work very well, so I was quite put out about that.  However, Feisty works quite well.  At this point, I really don't have any complaints.

BTW, I updated the first post at the very end for Multimedia setup.

---

### Post by rfrey74 on 2007-05-26
OK, I've been having difficulties with the wireless networking, but I have finally figured out a work around.  I have edited the first post with said workaround.  It is in the Drivers section where it deals with the wireless setup.

---

### Post by willistg on 2007-06-30
Is your ext mic working? mine is not. int mic sounds like poop too. 

Also, at least for me putting in ndis and blacklisting bcm* made the machine lockup on next boot.

---

### Post by rfrey74 on 2007-07-11
Sorry it took me so long to reply to this.

I haven't tested the mics.  However, if you are getting capture, but it is distorted (sounds like poop), then you may just need to turn the gain down on the microphone.  You should be able to adjust the capture level of the microphone through the gnome-volume-control.  If the gain is too hot, it will clip.

As far as not being able to boot, I don't know why ndis and blacklisting bcm43xx causes a lockup.  That seems odd to me.  Try using the boot parameter noapic.  That should help.

---

### Post by rube1947 on 2007-07-19
I have tried to install feisty on my HP dv9000z and all I get at the end of the set up is the silver screen of death. Any thoughts.  I have Vista on the machine and I am desperate to put a usable OS on the machine or I fear I will have to throw it away.  Thanks

---

### Post by rfrey74 on 2007-07-24
Have you tried putting "noapic" in your boot parameters?

---

