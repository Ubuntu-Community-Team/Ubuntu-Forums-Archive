---
title: "how to I enable my wirless on Ubuntu 8.10"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by waheedrafiq on 2009-03-14
here is my system info :

waheed@waheed-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff) 
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22) 


my problem is how do I enable my wireless network ? is there any easy user interface.

---

### Post by sp0nge on 2009-03-14
Are you certain the wireless drivers are working? Please post the output of:

```
iwconfig
```

Also, is there any networking icon available? Try to click/right click on that and see if you find the "enable wireless" option.

---

### Post by waheedrafiq on 2009-03-15
waheed@waheed-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

waheed@waheed-laptop:~$


the above is the out come of iwconfig


what does it mean ??

---

### Post by lisati on 2009-03-15
> **waheedrafiq said:**
> 
what does it mean ??

I think it means that your networking isn't picking up anything.

The following command should show if anything's detectable: ```
iwlist scan
```

---

### Post by waheedrafiq on 2009-03-15
this is the out come

 waheed@waheed-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

waheed@waheed-laptop:~$ 

I have a Advent latop the mini notebook 

waheed@waheed-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
waheed@waheed-laptop:~$

help

---

### Post by Kevbert on 2009-03-15
Please take a look at [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187"). It looks like you don't have a wireless driver installed.

---

### Post by ugm6hr on 2009-03-15
You need this:
[http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html](http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html)
[http://boskastrona.ovh.org/?page=2](http://boskastrona.ovh.org/?page=2)

Select the appropriate .deb (for the correct Intrepid kernel. e.g. [email]linux-rtl8187se-modules-04coffee@2.6.27.7.11.deb[/email] for 2.6.27-7) and double-click.

Hopefully that should work.

---

