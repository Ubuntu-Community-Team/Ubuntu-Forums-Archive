---
title: "acer one ZG5 crd reader won't read XD"
date: 2009-10-31
forum: Hardware
---

### Post by gleble on 2009-10-31
I am using Jaunty 9.04 and Acer Aspire One ZG5. I cannot get the card reader to read XD cards. Can anyone help?

---

### Post by gleble on 2009-11-01
This is the output of lspci. I can't see any mention of the cardreader.

Help!

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

---

### Post by teh603 on 2009-11-01
Is it in the reader when you first turn on the system? That often helps.

---

### Post by gleble on 2009-11-03
Yes it has the card in the right hand reader on startup. An XD card doesn't seem to fit in the left one. I've done another lspci and its got the following lines.
```
01:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
01:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
01:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
01:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
```
The last one is interesting. Do I need a JMicron? If so how do I find one?

---

### Post by bailout on 2009-11-03
Have alook at the aao forums as well.

[http://www.aspireoneuser.com/forum/viewforum.php?f=28&sid=be0300c0c0bb18ed09ad390caff757a2](http://www.aspireoneuser.com/forum/viewforum.php?f=28&sid=be0300c0c0bb18ed09ad390caff757a2)

I don't think any distro has full functionality on the card readers except linpus.

---

### Post by teh603 on 2009-11-03
> **bailout said:**
> I don't think any distro **is willing to use binary blob drivers** on the card readers except linpus.Corrected, since I'm pretty sure that the Linpus drivers are binary blobs. If they weren't, then we'd probably all have full functionality by now.

---

### Post by gleble on 2009-11-04
Do I take it then that Linpus drivers won't run on Jaunty?
Any other ideas?

---

### Post by darkshadow on 2009-11-04
new acer laptop's use pcie hotplugging when a card is inserted but it is not setup right so the kernel does not see it there is a fix

add "pciehp.pciehp_force=1" to the kernel line in grub then it always works without that the card reader only works with a card inserted at boot time

That well fix one problem but I don't know the state of the XD drivers because last I checked they where bad but that was along time ago since I only use SD cards.

---

### Post by gleble on 2009-11-05
I've tried that and it doesn't work for XD cards. I haven't got an SD to test it.

---

### Post by darkshadow on 2009-11-05
Wow XD drivers are still that bad since last time I checked was 2006 but you do need that pciehp stuff just for the card reader to work in general on that laptop.

---

### Post by saint_s on 2010-02-06
[FONT=monospace]xd card driver for jmb38x 

[/FONT][http://ubuntuforums.org/showthread.php?t=1313137&page=4](http://ubuntuforums.org/showthread.php?t=1313137&page=4)


Regards 

saint_s[FONT=monospace][/FONT]

---

