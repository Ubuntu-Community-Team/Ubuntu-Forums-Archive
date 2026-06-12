---
title: "Mouse, Keyboard Freeze on Lenovo Y500"
date: 2008-08-27
forum: Hardware
---

### Post by sas3 on 2008-08-27
I just installed Ubunutu 8.04 64bit on my Lenovo Y500 (Celeron-M 520, 512MB RAM, 80GB SATA HDD, GMA950 Integrated graphics, 15.4" wide screen).

Whenever I Power-On the system the Keyboard and Mouse freeze (the welcome/login screen comes up, but I can't login). 

The most consistent solution appears to be to first boot WindowsXP from another partition, restart the system and now Ubuntu works! (this morning, I had boot windows twice before Ubuntu started working).

I searched the forums, but couldn't find the solution; I am sorry if this was indeed posted, but if somehow missed it.

Please help.

--Sas3--

---

### Post by Crafty Kisses on 2008-08-27
Post the output of > lspci

---

### Post by sas3 on 2008-08-27
>>>> Output of lspci <<<<

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by sas3 on 2008-09-04
I am still stuck with this problem. I've posted the output of lspci, as requested.

Could someone help please?

Thank you.

--Sas3--

---

### Post by sameer.india on 2008-09-22
next time you face such a problem try using a usb mouse and keyboard
they work
or in the boot menu before selecting the OS press 'e' on your choice
3-4 lines appear on the line starting with kernel press 'e' again and type in 'i8042.reset' at its end and press enter then press 'b'
the touchpad and keyboard should work until you shutdown again
login 
then go to the terminal and do

sudo gedit /boot/grub/menu.lst

A text editor should open
scroll down till you reach the part where the contents of the boot menu are present.
Every ubuntu entry has a line starting with kernel
just type in i8042.reset at its end.

eg:-
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=80868411-3784-4dbe-9e5d-a44c72e81747 ro quiet splash i8042.reset
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

---

### Post by sas3 on 2008-10-07
Thank you sameer.india... I have been away for a while and saw your message just now. I will try it and post the result here.

---

### Post by puttux on 2008-10-15
> **sameer.india said:**
> next time you face such a problem try using a usb mouse and keyboard
they work
or in the boot menu before selecting the OS press 'e' on your choice
3-4 lines appear on the line starting with kernel press 'e' again and type in 'i8042.reset' at its end and press enter then press 'b'
the touchpad and keyboard should work until you shutdown again
login 
then go to the terminal and do

sudo gedit /boot/grub/menu.lst

A text editor should open
scroll down till you reach the part where the contents of the boot menu are present.
Every ubuntu entry has a line starting with kernel
just type in i8042.reset at its end.

eg:-
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=80868411-3784-4dbe-9e5d-a44c72e81747 ro quiet splash i8042.reset
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

That worked really great... Thanks a lot. 
Could you explain what exactly is happening inside when we add this kernel argument?
thanks again

---

### Post by tejaswiganesh on 2009-11-22
Thanks a lot... This workaround helped me to fix my friend's ubuntu 9.10.

---

### Post by nuku_da2 on 2009-11-22
Hello,

I've upgraded from Ubuntu 9.04 to Ubuntu 9.10 and I have the same problem, and I can't fix it. I have been reading and trying possible solutions during more than a hour, but my touchpad doesn't work. My laptop is a HP Pavilion dv6000.

The output of lspci is:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


Can anyone help me, please?

---

### Post by soumyamandi on 2010-02-25
> **nuku_da2 said:**
> Hello,

I've upgraded from Ubuntu 9.04 to Ubuntu 9.10 and I have the same problem, and I can't fix it. I have been reading and trying possible solutions during more than a hour, but my touchpad doesn't work. My laptop is a HP Pavilion dv6000.

The output of lspci is:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


Can anyone help me, please?

refer to the solution posted by sameer.india ! It worked for me in karmic.

---

### Post by ankitiitkee on 2010-06-13
Hi , I have the same problem of touchpad nonfunctioning in ubuntu 10.04
I tried sameer's solution of pressing e and then adding i8042.reset before choosing os for booting ....and wonderfully it worked.. but the way to permanent solve the problem    .....
there is no menu.lst file in /boot/grub ......guide me further

---

### Post by ankitiitkee on 2010-06-13
I have lenovo y500 laptop and using ubuntu 10.04 
For so long  I was facing the same problem of touchpad not working.
This post kindled a hope. I tried 
"r in the boot menu before selecting the OS press 'e' on your choice"
and adding i8042.reset. ...it worked wonderfully.
but just about the permanent solution there is no file called menu.lst in grub folder..

Please guide me further

---

### Post by elr0y on 2010-06-26
> **ankitiitkee said:**
> I have lenovo y500 laptop and using ubuntu 10.04 
For so long  I was facing the same problem of touchpad not working.
This post kindled a hope. I tried 
"r in the boot menu before selecting the OS press 'e' on your choice"
and adding i8042.reset. ...it worked wonderfully.
but just about the permanent solution there is no file called menu.lst in grub folder..

Please guide me further

I'm not an expert, but you are probably using grub2. 
See here for more about grub2: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

From that link: "The Grub 2 user-configurable settings are contained mainly in /etc/default/grub"

Hope that helps. 

I'm still having a freezing problem myself in 10.04, but haven't tried any of the many solutions I've read....

---

