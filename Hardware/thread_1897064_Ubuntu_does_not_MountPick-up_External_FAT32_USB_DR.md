---
title: "Ubuntu does not Mount/Pick-up External FAT32 USB DRIVE"
date: 2011-12-18
forum: Hardware
---

### Post by SILLAT on 2011-12-18
I have a Western Digital FAT32 USB Portable Hard Drive that i use to store important files that ubuntu will not mount or recognise.
The Drive works on WINXP and it also works on a Ubuntu Laptop that i have running 10.04LTS but on my main desktop (Ubuntu 10.10) nothing happens.
I have read on many forums people having the same problem i have tried some of the options but none seems to work..
The problem that i am having is that when the computer boots its says "unable to enumerate USB device on port 4,5,6..."
I tried ubuntu 11.10 Live CD and its the same problem, makes no sense upgrading... am confused now

If I Run dmesg

 6274.640032] usb 5-1: new low speed USB device using uhci_hcd and address 18
[ 6274.764020] usb 5-1: device descriptor read/64, error -71
[ 6274.992032] usb 5-1: device descriptor read/64, error -71
[ 6275.208032] usb 5-1: new low speed USB device using uhci_hcd and address 19
[ 6275.332030] usb 5-1: device descriptor read/64, error -71
[ 6275.556032] usb 5-1: device descriptor read/64, error -71
[ 6275.772030] usb 5-1: new low speed USB device using uhci_hcd and address 20
[ 6276.180022] usb 5-1: device not accepting address 20, error -71
[ 6276.292072] usb 5-1: new low speed USB device using uhci_hcd and address 21
[ 6276.700022] usb 5-1: device not accepting address 21, error -71
[ 6276.700045] hub 5-0:1.0: unable to enumerate USB device on port 1
[ 6276.812030] usb 5-2: new full speed USB device using uhci_hcd and address 22
[ 6276.932046] usb 5-2: device descriptor read/64, error -71
[ 6277.156029] usb 5-2: device descriptor read/64, error -71
[ 6277.372030] usb 5-2: new full speed USB device using uhci_hcd and address 23
[ 6277.492031] usb 5-2: device descriptor read/64, error -71
[ 6277.716028] usb 5-2: device descriptor read/64, error -71
[ 6277.932031] usb 5-2: new full speed USB device using uhci_hcd and address 24
[ 6278.340027] usb 5-2: device not accepting address 24, error -71
[ 6278.452031] usb 5-2: new full speed USB device using uhci_hcd and address 25
[ 6278.860021] usb 5-2: device not accepting address 25, error -71
[ 6278.860044] hub 5-0:1.0: unable to enumerate USB device on port 2
[ 6280.028111] usb 1-4: new high speed USB device using ehci_hcd and address 64
[ 6280.556028] usb 1-4: device not accepting address 64, error -71
[ 6280.612263] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6281.252035] usb 1-4: new high speed USB device using ehci_hcd and address 66
[ 6281.772017] usb 1-4: device not accepting address 66, error -71
[ 6281.828308] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6282.484033] usb 1-4: new high speed USB device using ehci_hcd and address 68
[ 6283.008033] usb 1-4: device not accepting address 68, error -71
[ 6283.064226] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6283.708033] usb 1-4: new high speed USB device using ehci_hcd and address 70
[ 6284.236022] usb 1-4: device not accepting address 70, error -71
[ 6284.292270] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6284.933258] usb 1-4: new high speed USB device using ehci_hcd and address 72
[ 6285.452020] usb 1-4: device not accepting address 72, error -71
[ 6285.508314] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6286.156032] usb 1-4: new high speed USB device using ehci_hcd and address 74
[ 6286.680028] usb 1-4: device not accepting address 74, error -71
[ 6286.736235] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6287.380031] usb 1-4: new high speed USB device using ehci_hcd and address 76
[ 6287.908024] usb 1-4: device not accepting address 76, error -71
[ 6287.964279] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6288.600034] usb 1-4: new high speed USB device using ehci_hcd and address 78
[ 6289.120022] usb 1-4: device not accepting address 78, error -71
[ 6289.176198] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6289.820030] usb 1-4: new high speed USB device using ehci_hcd and address 80
[ 6290.348021] usb 1-4: device not accepting address 80, error -71
[ 6290.404242] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6291.048033] usb 1-4: new high speed USB device using ehci_hcd and address 82
[ 6291.576079] usb 1-4: device not accepting address 82, error -71
[ 6291.632286] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6292.272053] usb 1-4: new high speed USB device using ehci_hcd and address 84
[ 6292.792018] usb 1-4: device not accepting address 84, error -71
[ 6292.848206] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6293.496030] usb 1-4: new high speed USB device using ehci_hcd and address 86
[ 6294.024016] usb 1-4: device not accepting address 86, error -71
[ 6294.080250] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6294.732074] usb 1-4: new high speed USB device using ehci_hcd and address 88
[ 6295.256023] usb 1-4: device not accepting address 88, error -71
[ 6295.312719] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6295.976032] usb 1-4: new high speed USB device using ehci_hcd and address 90
[ 6296.500022] usb 1-4: device not accepting address 90, error -71
[ 6296.556213] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6297.200034] usb 1-4: new high speed USB device using ehci_hcd and address 92
[ 6297.728027] usb 1-4: device not accepting address 92, error -71
[ 6297.784257] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6298.424034] usb 1-4: new high speed USB device using ehci_hcd and address 94
[ 6298.949378] usb 1-4: USB disconnect, address 94
[ 6300.092032] usb 1-4: new high speed USB device using ehci_hcd and address 95

$ tail -f /var/log/messages

Dec 18 11:02:53 OneWorld kernel: [ 6331.588031] usb 1-4: new high speed USB device using ehci_hcd and address 15
Dec 18 11:02:53 OneWorld kernel: [ 6331.766802] usb 1-4: USB disconnect, address 15
Dec 18 11:02:54 OneWorld kernel: [ 6332.908032] usb 1-4: new high speed USB device using ehci_hcd and address 16
Dec 18 11:02:55 OneWorld kernel: [ 6334.132329] usb 1-4: new high speed USB device using ehci_hcd and address 18
Dec 18 11:02:56 OneWorld kernel: [ 6335.400032] usb 1-4: new high speed USB device using ehci_hcd and address 20
Dec 18 11:02:58 OneWorld kernel: [ 6336.660032] usb 1-4: new high speed USB device using ehci_hcd and address 22
Dec 18 11:02:58 OneWorld kernel: [ 6337.136954] usb 1-4: USB disconnect, address 22
Dec 18 11:02:59 OneWorld kernel: [ 6338.280032] usb 1-4: new high speed USB device using ehci_hcd and address 23
Dec 18 11:03:01 OneWorld kernel: [ 6339.508034] usb 1-4: new high speed USB device using ehci_hcd and address 25
Dec 18 11:03:02 OneWorld kernel: [ 6340.732032] usb 1-4: new high speed USB device using ehci_hcd and address 27
Dec 18 11:03:03 OneWorld kernel: [ 6341.956031] usb 1-4: new high speed USB device using ehci_hcd and address 29
Dec 18 11:03:04 OneWorld kernel: [ 6343.228030] usb 1-4: new high speed USB device using ehci_hcd and address 31
Dec 18 11:03:05 OneWorld kernel: [ 6344.448033] usb 1-4: new high speed USB device using ehci_hcd and address 33
Dec 18 11:03:07 OneWorld kernel: [ 6345.676030] usb 1-4: new high speed USB device using ehci_hcd and address 35
Dec 18 11:03:08 OneWorld kernel: [ 6346.900027] usb 1-4: new high speed USB device using ehci_hcd and address 37
Dec 18 11:03:09 OneWorld kernel: [ 6348.136318] usb 1-4: new high speed USB device using ehci_hcd and address 39
Dec 18 11:03:10 OneWorld kernel: [ 6349.364034] usb 1-4: new high speed USB device using ehci_hcd and address 41

$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Any Help Appreciated to troubleshoot this problem..
Thanks Much

---

### Post by sudodus on 2011-12-18
It works on XP but not Ubuntu 11.10 on the same computer? I'm asking to find out if it could be a hardware error. What if you move to another USB connector? It might also be worth trying 'manual mounting' with mount (but it won't work if the device is not found at all).
```

sudo mkdir /mnt/usb-wd  # only once
sudo mount /dev/sd[COLOR=Red]f1[/COLOR] -t auto /mnt/usb-wd
``` Substitute [COLOR=Red]f1[/COLOR] with the appropriate characters!

But I know that there are problems with the newest version. Such problems will be solved after some weeks or months. A simple way to avoid such problems is to wait with dist-upgrades at least 3 months after a version is released or to test all important things with a live system.

If this problem and maybe others are too big, I suggest that you backup your personal files (dokuments, photos, videos, music ...) and reinstall an older version, 10.04 LTS or 11.04.

---

### Post by SILLAT on 2011-12-18
> **sudodus said:**
>  I'm asking to find out if it could be a hardware error. What if you move to another USB connector?  .

Hey Thanks Much
Jus tried another USB cord . . It now sees the Drive what's the next step
I find it funny that the same USB cord work on On the other Pc's but not on the current PC experiencing the problem.

This is the Output when i Run lsusb it now sees the drive
~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 075: ID 13fd:160e Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by sudodus on 2011-12-18
Run sudo ```

sudo fdisk -lu   # and
df               # and
sudo blkid
``` and post the result

---

### Post by SILLAT on 2011-12-18
> **sudodus said:**
> Run sudo ```

sudo fdisk -lu   # and
df               # and
sudo blkid
``` and post the result

Results dont look too good.. but here goes

~# sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002825b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    38086655    19042304   83  Linux
/dev/sda2        38088702   234440703    98176001    5  Extended
/dev/sda5        38088704    42969087     2440192   82  Linux swap / Solaris
/dev/sda6        42971136   234440703    95734784   83  Linux
root@World:~# df  
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             18743164   4397184  13393868  25% /
none                    377596       232    377364   1% /dev
none                    383220       264    382956   1% /dev/shm
none                    383220       212    383008   1% /var/run
none                    383220         0    383220   0% /var/lock
/dev/sda6             94231428  28793996  60650696  33% /home
root@World:~# sudo blkid
/dev/sda1: UUID="20df8811-2e90-4664-832f-2f2755954fb8" TYPE="ext4" 
/dev/sda5: UUID="32b5b7a2-895f-4cf7-832f-9da43001f40e" TYPE="swap" 
/dev/sda6: UUID="7e090e0b-4200-4841-ad72-2d87c9b19172" TYPE="ext3"

---

### Post by sudodus on 2011-12-18
> **SILLAT said:**
> Results dont look too good.. but here goes
...
No fdisk can not see it (yet). Have you rebooted your computer since you changed to the working usb cable?

*Edit: If this problem and maybe others are too big, I suggest that you backup  your personal files (dokuments, photos, videos, music ...) and reinstall  an older version, 10.04 LTS or 11.04. Whatever version you choose, try it live from the installation CD or USB drive to test that all important things work before installation. I run different systems but my 'work-horse' is Ubuntu 10.04 LTS. I suggest you try it on this machine. After all, you have it already on the laptop. If everything important works (drivers to various periferal devices), install it and keep it until end of life (April 2013)!*

---

### Post by SILLAT on 2011-12-18
Ever since i rebooted the PC it will not show up when i run lsusb, i dont know what is the problem but am confused now.
I think am gonna just gonna move my files to another drive format the drive that is giving trouble an have a go at it again. I know for sure the drive is working but i dont know if its the MOBO/BIOS/Kernel/Ubuntu incompatibilities that's rendering it unusable.
Will keep you posted
For the record i tried running a Live Cd of Ubuntu 8.04/10.04 on it and its the same problem on the PC but it works on the Laptop running 10.04.
Thanks Much

---

### Post by sudodus on 2011-12-18
I think it is something strange with the hardware on the pc. Obviously it works with XP, but not with Ubuntu versions, that see it from your laptop. Such problems can be very hard to solve.

Anyway, good luck :-)

---

