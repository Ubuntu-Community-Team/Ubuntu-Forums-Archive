---
title: "Seagate 500GB external USB drive"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by ddover on 2007-04-05
ubuntu 7.04
kernel 2.6.20


Upon plugging in my drive Ubuntu does nothing. I have tried the drive on other computers and it works. It is detected according to lsusb 

Here is the output of  dmesg

[ 1109.171501] usb 5-2: new high speed USB device using ehci_hcd and address 2
[ 1109.787281] usb 5-2: configuration #1 chosen from 1 choice
[ 1109.855608] usbcore: registered new interface driver libusual
[ 1109.878524] Initializing USB Mass Storage driver...
[ 1109.878630] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1109.878699] usb-storage: device found at 2
[ 1109.878705] usbcore: registered new interface driver usb-storage
[ 1109.878711] USB Mass Storage support registered.
[ 1109.878714] usb-storage: waiting for device to settle before scanning
[ 1114.864698] usb-storage: device scan complete
[ 1115.346323] scsi 4:0:0:0: Direct-Access     ST350064 1A               3.AA PQ: 0 ANSI: 0
[ 1115.348045] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[ 1115.349042] sdb: Write Protect is off
[ 1115.349047] sdb: Mode Sense: 10 00 00 00
[ 1115.349053] sdb: assuming drive cache: write through
[ 1115.349913] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[ 1115.350912] sdb: Write Protect is off
[ 1115.350917] sdb: Mode Sense: 10 00 00 00
[ 1115.350921] sdb: assuming drive cache: write through
[ 1115.350924]  sdb: sdb1
[ 1115.358218] sd 4:0:0:0: Attached scsi disk sdb
[ 1115.358271] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1797.107759] usb 5-2: USB disconnect, address 2
[ 1862.394658] usb 5-1: new high speed USB device using ehci_hcd and address 3
[ 1863.010328] usb 5-1: configuration #1 chosen from 1 choice
[ 1863.010820] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1863.010981] usb-storage: device found at 3
[ 1863.010986] usb-storage: waiting for device to settle before scanning
[ 1867.995994] usb-storage: device scan complete
[ 1868.477745] scsi 5:0:0:0: Direct-Access     ST350064 1A               3.AA PQ: 0 ANSI: 0
[ 1868.479009] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[ 1868.479955] sdb: Write Protect is off
[ 1868.479960] sdb: Mode Sense: 10 00 00 00
[ 1868.479966] sdb: assuming drive cache: write through
[ 1868.480826] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[ 1868.481824] sdb: Write Protect is off
[ 1868.481829] sdb: Mode Sense: 10 00 00 00
[ 1868.481834] sdb: assuming drive cache: write through
[ 1868.481837]  sdb: sdb1
[ 1868.531142] sd 5:0:0:0: Attached scsi disk sdb
[ 1868.531195] sd 5:0:0:0: Attached scsi generic sg2 type 0
$ 

thanks in advance for any advice you might have.

---

### Post by johnc4510 on 2007-04-05
I think you need to mount the volume, but someone else will have to give you the commands.  Consider this a bump.

---

### Post by ddover on 2007-04-05
Solved

mkdir /mnt/harddrive
mount -t vfat /dev/sda1 /mnt/harddrive

thanks :)

---

### Post by larryi5 on 2008-04-12
Got some n00b questions. Do you enter that script in the terminal, and will it reformat my external? cuz id like to keep everything thats on it lol

---

### Post by EyePeaSea on 2008-04-12
> **larryi5 said:**
> Got some n00b questions. Do you enter that script in the terminal, and will it reformat my external? cuz id like to keep everything thats on it lol

Yes, you would enter those commands into a terminal window.  You *may* need to be root (administrator level), so try adding 'sudo' to the start of the line and then put in the root (admin) password when prompted.

The mount command just 'presents' the disk so that you can find it.  The contents of the disk will end up below '/mnt/harddrive'.  It will *not* format your drive - your data is safe.

Just to teach my grandmother to suck eggs - the actual mount command will probably be different from one person to the next.  Sometimes, the external disk may be seen as /dev/sda1,  other times it may be /dev/sdb1 etc. etc.)

---

### Post by larryi5 on 2008-04-12
> **EyePeaSea said:**
> Yes, you would enter those commands into a terminal window.  You *may* need to be root (administrator level), so try adding 'sudo' to the start of the line and then put in the root (admin) password when prompted.

The mount command just 'presents' the disk so that you can find it.  The contents of the disk will end up below '/mnt/harddrive'.  It will *not* format your drive - your data is safe.

Just to teach my grandmother to suck eggs - the actual mount command will probably be different from one person to the next.  Sometimes, the external disk may be seen as /dev/sda1,  other times it may be /dev/sdb1 etc. etc.)

Im having trouble with the root login thing. My HDD also gave me some commands to type in and it still didnt work cuz i need to be logged in or whatever. heres a screenie

[http://www.imgsync.com/data/img/9256594hdd_trouble.png](http://www.imgsync.com/data/img/9256594hdd_trouble.png)

---

### Post by larryi5 on 2008-04-12
larryi5@Saggy-Clit:~$ sudo root
[sudo] password for larryi5: [i type my pass]
sudo: root: command not found
larryi5@Saggy-Clit:~$ 


what the heck lol

---

### Post by larryi5 on 2008-04-19
Hello

---

### Post by xboxbman on 2008-04-28
> **larryi5 said:**
> Hello

type ```
sudo -s
``` then enter the commands after the password prompt

---

