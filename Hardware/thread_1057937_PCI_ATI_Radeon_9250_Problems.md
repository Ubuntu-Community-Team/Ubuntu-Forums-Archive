---
title: "PCI ATI Radeon 9250 Problems"
date: 2009-02-02
forum: Hardware
---

### Post by jeremey on 2009-02-02
Hi, I am having some problems getting my PCI ATI Radeon 9250 to work.  I recently put Xubuntu 8.10 on my [Compaq Presario SR1103WM]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00063244&lc=en&dlc=es&cc=pe&product=424182").  It wouldn't install until I took that card out and just used the integrated video card.  Now when I put the ATI card in and try to boot up, the system hangs where the bar is about 1/4 inch from the end before the login screen comes up.  Its frustrating because the internal card is only about 64megs, and the card I am trying to use has 256mb.

---

### Post by khelben1979 on 2009-02-02
Are you able to get to a text console? ```
ctrl + alt + f1
```

---

### Post by jeremey on 2009-02-02
I can before it hangs up, if I wait until it hangs, it freezes the keyboard.  When its going through its thing, it comes up with a bunch of Segmentation Faults, then the whole system just freezes.  I can still force reboot with the ctrl-alt-prtscr reisub though, but nothing else.  The bios has a setting for primay display - onboard or pci, onboard works fine, it just doesn't like the PCI card.

---

### Post by jeremey on 2009-02-04
:sigh:

After some searching and thread reading, I followed the directions on this page, [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html") and it still doesn't work...

The "sudo dpkg-reconfigure xserver-xorg" doesn't ever ask for detection of video.


if helpful, my lspci output:

jeremey@Desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:09.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:09.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:0a.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)
01:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
jeremey@Desktop:~$

---

### Post by khelben1979 on 2009-02-04
I believe that you might have success by using a different kernel.

Is it Ubuntu 8.10 "Intrepid" you are trying it with?

---

### Post by jeremey on 2009-02-05
Release 8.10 (intrepid)
Kernel Linux 2.6.27-11-generic

---

### Post by jeremey on 2009-02-05
Is there a way to see the boot log, like windows' bootlog.txt?  Because I'd like to see what is happening before the point of it freezing, and I'm not too sure how to do that.

---

### Post by khelben1979 on 2009-02-05
Use the dmesg command:

```
sudo dmesg
```

In /var/log you have the place where logfiles are written.

---

### Post by shadowhacker on 2009-02-05
I should think your next step would be to blacklist the driver Ubuntu is trying to load for it. That way you can at least boot with it installed and start trying drivers. I would help with editing the blacklist file, but my Ubuntu partition is currently down on an unrelated matter.

---

