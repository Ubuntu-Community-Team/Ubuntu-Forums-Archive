---
title: "Itronix XR-1 XR270 Gobook sound &amp; networking issues"
date: 2015-06-21
forum: Hardware
---

### Post by neb8 on 2015-06-21
After installing Lubuntu 15.04 to a XR-270 Gobook there exists some issues with sound and networking.

Having no sound and recognition of the NIC appears to be an installation problem with their drivers.

Known problems after installation.

Networking (hardwired) ____

 Agere Systems ET-131x PCI-E Gigabit Ethernet
 Ethernet controller: LSI Corporation ET-131x PCI-E Ethernet Controller (rev 01)

Ethernet controller is recognized as "UNCLAIMED" and unable to initialize. 

Sound __

Realtek High Definition Audio
Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)

Attempted driver re-installation using the Realtek Linux driver 0001-LinuxPkg_5.18rc8.tar

[http://www.realtek.com.tw/downloads/downloadsview.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsview.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)

The sound card driver installation seemed to be successful along with a few warnings.

As previously, the sound card is recognized and the sound card and driver seems to be installed, however there's no sound. (sound controls checked, inputs and outputs enabled, nothing is muted, etc.) 

Note: Sound card and NIC work just fine under Windows XP.

---

### Post by Yellow Pasque on 2015-06-22
Both should work "out of the box" and should have modules/drivers available on (L)Ubuntu 15.04. They are included in the kernel.

For the e thernet try loading the kernel module manually and checking dmesg for errors afterwards:
```
sudo modinfo et131x
sudo modprobe -v et131x
dmesg | tail -n 20
sudo ifconfig -a
```

As for audio, installing the Realtek Linux audio driver is usually a bad idea (this isn't Windows). Do your best to install it and get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by neb8 on 2015-06-23
[QUOTE=Temüjin;13308598]Both should work "out of the box" and should have modules/drivers available on (L)Ubuntu 15.04. They are included in the kernel.

For the e thernet try loading the kernel module manually and checking dmesg for errors afterwards:
```
sudo modinfo et131x
sudo modprobe -v et131x
dmesg | tail -n 20
sudo ifconfig -a
```

For another reason I needed to re-install Lubuntu. After a second attempt to initialize the hardwire NIC the above commands would not load the et131x driver.
For some reason the et131x module won't load. Adding et131x to the /etc/modules file has no effect.
lsmod shows that et131x is still set to 0.
I could find no reference to et131x in the blacklist folder.
When using ifconfig only the wireless adapter is recognized.
lspci does display all the of  hardware adapters.

Ethernet controller: LSI Corporation ET-131x PCI-E Ethernet Controller (rev 01)
* Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)

* recognized and working

The latest driver source code found was developed under Ubuntu 11.04. There are downloadable source codes developed and tested under other versions of Linux other than Ubuntu.

Apparently the et131x NIC compiled Ubuntu driver support is limited to  11.04 and 11.10 Ubuntu OS installation drivers. The NIC and driver seems to have better performance under 11.10, after doing an OS non-dist upgrade. The OS installation driver didn't function under Ubuntu 12.10.

The driver source probably needs to be updated then re-compiled to work under later versions of Ubuntu.

---

