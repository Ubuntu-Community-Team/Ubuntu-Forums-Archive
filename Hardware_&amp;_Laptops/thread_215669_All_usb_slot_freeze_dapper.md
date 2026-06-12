---
title: "All usb slot freeze dapper"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by Bleeps on 2006-07-14
Hi,

I've a little problem with the Dapper Release after the update of breezy! When i put a usb drive in a slot the system freeze ! 
Before with breezy release i never had this problem ! 

So, i tested with  cd live (of shipping support) and the bug is similar. If i put a usb keys, a camera, or something like that, my system freeze and i can do anything !

I tested with other kernel, but problem isn't fixed !
I search some help in Ubuntu forum's France but anybody find an answer at my problem ! 

If anybody can help me, i have a amd with azrock motherboard !

//  More infos : 

johan@Johan:~$ uname -a
Linux Johan 2.6.15-26-386 #1 PREEMPT Fri Jul 7 19:27:00 UTC 2006 i686 GNU/Linux
johan@Johan:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 02)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media I O] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa st Ethernet (rev 90)
0000:00:0c.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440  AGP 8x] (rev a4)
johan@Johan:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

// Thx a lot, and sorry for my suck's english ! (i hope you can understand](*,)  me)

---

### Post by eaque on 2006-07-24
Up !

I have the same problem, and it's really disturbing !:(

---

### Post by Bleeps on 2006-08-04
A little up fo any help :)
Because it's really sad if i'll be change of distrib only for that =/

---

### Post by mondocannibale on 2006-09-18
hi,

the same problem here. as soon as i put something in any usb-slot the system freezes. i've tried fedora core 5 & windows before, where it worked very well.
maybe the mainboard is the cause. I've got a similar one (K7S8XE)

```

thorsten@thorsten-desktop:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

Any helpful suggestions???!
mondo

---

### Post by mondocannibale on 2006-09-20
ok, I found out how to avoid the problem:

you have to deactivate "USB 2.0 support" in BIOS chip-settings.
then the system won't freeze anymore.

---

### Post by Bleeps on 2006-10-22
For fix the problem !

```
blacklist ehci_hcd
```
in /etc/modprobe.d/blacklist

After reboot and when you'are reboot make 

```
 sudo modprobe -r ehci_hcd 
```

And you can use you're usb keys, but make 

```
sudo modprobe -r ehci_hcd
```

All time after reboot if you want to use usb key's :)

I hope this bug will be fix in edgy :KS

---

