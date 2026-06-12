---
title: "looking for module for my thinkpad t40p"
date: 2010-01-13
forum: Hardware
---

### Post by B&amp;Co on 2010-01-13
Hi everybody!:P
I want to compile my own kernel for the laptot thinkpad t40p but, after a long search, I still can not find the right module for my ATA hd so I still get an error message at boot that advises me that the root filesystem can not be mounted...
Anybody know how to find out the right module?

PS thanks to all the linux community

Andrea

---

### Post by B&amp;Co on 2010-01-13
mmm... maybe it's better if I paste above the output of lspci in order to give some more informations...

```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
```

UPGRADE: I know that my ide controller needs the module colled piix (which on the 2.6.32 kernel is called BLK_DEV_PIIX) but even compiling the kernel with it the kernel still does not work

---

### Post by B&amp;Co on 2010-01-14
ok... I'll try to change my question...

I have a running ubuntu installation working fine with 2.6.24-16-386 prebuilt kernel, so i believe that all the modules needed by linux have been loaded. Now, how can I recognize the module for my ide controller between the modules listened by lsmod command?

Any suggestion?:(

---

### Post by Yellow Pasque on 2010-01-14
How do you know it's your IDE controller? It sound like you might not have the grub entry set right?

---

### Post by B&amp;Co on 2010-01-14
> **Temüjin said:**
> How do you know it's your IDE controller? It sound like you might not have the grub entry set right?

well... I had the same error when I compiled the kernel for another machine and I forgot the hd controller...

Plus the grub entry is the same that I use for the prebuilt kernel (that works well)...

---

### Post by B&amp;Co on 2010-01-14
ok... Now I want to consider the possibility of an error in the grub entry (as suggested by Temüjin) but I need help to find the error out...

here the entry for ubuntu in my grub menu.lst

```
title           Ubuntu 8.04.3 LTS, kernel 2.6.32.2forfry
root            (hd0,0)
kernel          /vmlinuz-2.6.32.2forfry root=UUID=3890b9f6-cd0b-441b-abf9-e78f05a5808f ro quiet splash
quiet

title           Ubuntu 8.04.3 LTS, kernel 2.6.32.2forfry (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.32.2forfry root=UUID=3890b9f6-cd0b-441b-abf9-e78f05a5808f ro single
```

(hd0,0) is the right partition where grub is installed and the label of the root of my ubuntu installation is right...

I don't know if it could change something but the grub partition is different from the root partition, could it be a problem for my custom kernel?

---

### Post by B&amp;Co on 2010-01-28
I really don't know what to do... I've tried many different kernel configuration but I still get this error 

```
Kernel panic-not syncing: VFS: Unable to mount root fs on unknow-block(0,0)
```

I don't know if there is an error in the kernel configuration or it's due to something else...

I accept ANY suggestion... ](*,)

---

