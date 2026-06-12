---
title: "System won't recognize pendrive"
date: 2010-11-10
forum: Hardware
---

### Post by Larkas on 2010-11-10
Hello there, guys! For some reason, Ubuntu isn't recognizing my pendrive. I already ran some tests:

```
~$ sudo fdisk -l

Disco /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificador do disco: 0xf2f1f2f1

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1        2432    19535008+   7  HPFS ou NTFS
/dev/sda2            2433        3651     9791162+   7  HPFS ou NTFS
/dev/sda3            3651        4864     9743361    5  Estendida
/dev/sda5            3651        4807     9278464   83  Linux
/dev/sda6            4807        4864      463872   82  Linux swap / Solaris
``````
~$ dmesg | grep usb
[    0.163380] usbcore: registered new interface driver usbfs
[    0.163403] usbcore: registered new interface driver hub
[    0.163469] usbcore: registered new device driver usb
[   28.981111] usbcore: registered new interface driver ndiswrapper
[   58.088874] usb 1-3: new high speed USB device using ehci_hcd and address 2
[  164.362720] usb 1-3: USB disconnect, address 2
[  423.344071] usb 1-2: new high speed USB device using ehci_hcd and address 3
``````
~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```As you can see from the last output, the system does see my DataTraveler, but I can find or mount it! Could someone please help me?

PS: I'm really new to Linux, detailed instructions would be greatly appreciated.

---

### Post by sikander3786 on 2010-11-10
Hi.

Are you sure the pendrive is in proper working condition. Did you check it with some other PC?

It would be handy to look in gparted or System > Administraion > Disk Utility and see if it is listed there and if it has some defined partitions at all.

---

### Post by Larkas on 2010-11-10
Hmmm, it is working fine, really. I have a Windows XP installed in this computer, and it recognizes the pendrive just fine. Also, I can boot from it, as I did when I was testing Ubuntu before installing it. Lastly, it works just fine with my desktop, which has Windows 7 installed, and with my brother's laptop, which runs on Mac OSX, so I'm pretty sure it's a problem in Ubuntu.

I went to System > Administraion > Disk Utility and it doesn't show the pendrive either. gparted isn't installed, should I get it?

---

### Post by Larkas on 2010-11-12
Ehm, any ideas, anyone? :/

---

### Post by Larkas on 2010-12-05
Sorry to revive this, but I still haven't been able to solve this issue. Could anyone please help me?

---

### Post by fuzzy_dba on 2010-12-06
I had the same problem on my 10.10 laptop. Then I changed to a different bank of the USB ports on the laptop and it works fine... Turned out to be a hardware issue with mu Dell D620.

---

### Post by Larkas on 2010-12-06
Hmmm, what do you mean by bank, a different set of USB ports? If that's the case, I tested all of them :/ And strange thing is, they all work fine on the Windows XP I keep as a backup boot. And like I said before, the system does see the pendrive, it simply doesn't interpret it as such.

---

