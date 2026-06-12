---
title: "Wireless not working on Dell Precision M70"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by cayblood on 2005-11-23
I just did a fresh installation of 5.10 and after changing to the nVidia drivers everything seems to be working fine.  However, I think that my built-in wireless device may have been turned off during installation (the BIOS had it set to hot-key mode).  After noticing that there was no apparent wireless device installed, I looked in the device manager.  Under 82801 PCI Bridge it has three unknown devices listed--two from Texas Instruments and one from Broadcom.  I'm thinking that these devices might be my wireless and my modem.  However, I don't have any idea how to get them working.  It may be that my modem is an unsupported winmodem, but I at least want to get my wireless working.  Any suggestions?

Thanks,
Carl

---

### Post by Lambert on 2005-11-23
If you run command iwconfig is there any information such as this

ath0      IEEE 802.11g  ESSID:"xxxx"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:46:1D:AB:DA
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/94  Signal level=-61 dBm  Noise level=-95 dBm
          Rx invalid nwid:33581  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

If yes then it just needs to be configured to your network. If no then you need to find a driver for the device.

---

### Post by cayblood on 2005-11-24
Thanks.  I didn't get any information when I ran iwconfig so I think I'm going to have to install Windows to see which driver it uses and then try to set up ndiswrapper with that driver.  What a pain!

---

### Post by Lambert on 2005-11-24
You don't have to do that as it may be the wrong driver any way.

Follow these instructions on finding your driver if you're going to use ndiswrapper.

**To identify the driver that you need, first identify the card you have with 'lspci' and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card that with 'lspci -n' corresponding to the first column of 'lspci' output. The PCI ID is third column or fourth in some distributions and of the form '104c:8400'. Now you need to get the Windows driver for this chipset. In the [_list_]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"), find out an entry for the same PCI ID and download the driver corresponding to it *(don't worry if the link is not under your exact card as many cards you the same chipsets)*. Unpack the Windows driver with unzip/cabextract/unshield tools and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). *(this is important as some drivers have a connection with the .sys file which makes the driver work properly)* If there are multiple INF/SYS files, you may look in the [list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files for example, TI drivers use BIN firmware files are all in one directory on your harddrive.**

---

### Post by 980045 on 2006-04-13
Ive just installed Ubuntu on my Dell Precision M70 and I am in the same position as cayblood - I think my wireless was switched of during the install - ive installed the drivers using ndiswrapper but the wireless wont switch on - do i have to rebuild with windows to switch the wireless on?

Its set in the bios to come on...

Regards

Dave

---

### Post by Ozzkar on 2006-04-14
does any body knows if there is a way to put an icon on the taskbar when the wireless network is acctive?

---

### Post by PriceChild on 2006-04-14
try gtk wifi

---

### Post by testube_babies on 2006-04-15
I've found this problem in both Breezy and Dapper.  After installing nVidia drivers, my wireless cards are not found.  Switching back to nv drivers and reinstalling the linux-kernel fixes the problem, but I would really like to have accellerated drivers!  Has anyone had any luck with ndiswrapper?  I haven't.

---

### Post by testube_babies on 2006-04-16
Has anyone tried [this howto]("http://www.ubuntuforums.org/showthread.php?t=105437")?  I'm debating whether or not to try it, but it seems to modify the boot loader so I don't want to mess up my machine...

---

### Post by 980045 on 2006-04-18
Ive not tried that howto yet - do you also have a dellm70 testtube_babies?

---

