---
title: "Problems with USB stick"
date: 2014-11-12
forum: Hardware
---

### Post by drpsy on 2014-11-12
Hey guys,
I'm new to this forum and not a native english speaker, so please excuse me if I'm making mistakes.

My Problem is: I tried to generate a gparted-live USB stick, using the makeboot.bat file. After doing so, I cannot access the device anymore. After googling quite some time I tried the following:
 
```
christoph@server:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 048d:1168 Integrated Technology Express, Inc.


christoph@server:~$ dmesg | grep usb
[    0.144370] usbcore: registered new interface driver usbfs
[    0.144418] usbcore: registered new interface driver hub
[    0.144504] usbcore: registered new device driver usb
[    0.690842] usbcore: registered new interface driver libusual
[  243.632068] usb 1-3: new high-speed USB device number 2 using ehci_hcd
[  243.811824] scsi2 : usb-storage 1-3:1.0
[  243.812164] usbcore: registered new interface driver usb-storage


christoph@server:~$ dmesg | tail -20
[   10.915124] init: failsafe main process (529) killed by TERM signal
[   10.961495] type=1400 audit(1415827340.403:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=742 comm="apparmor_parser"
[   10.962357] type=1400 audit(1415827340.403:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=742 comm="apparmor_parser"
[   10.962793] type=1400 audit(1415827340.403:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=742 comm="apparmor_parser"
[   10.968766] type=1400 audit(1415827340.411:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=744 comm="apparmor_parser"
[   11.300224] init: plymouth-upstart-bridge main process (458) killed by TERM signal
[   12.606092] psmouse serio2: hgpk: ID: 10 00 64
[   15.871963] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   16.092170] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input7
[   19.520211] eth0: no IPv6 routers present
[  199.788343] e1000: eth0 NIC Link is Down
[  243.632068] usb 1-3: new high-speed USB device number 2 using ehci_hcd
[  243.811527] Initializing USB Mass Storage driver...
[  243.811824] scsi2 : usb-storage 1-3:1.0
[  243.812164] usbcore: registered new interface driver usb-storage
[  243.812173] USB Mass Storage support registered.
[  244.812933] scsi 2:0:0:0: Direct-Access     XXXXXXXX U168CONTROLLER   0.00 PQ: 0 ANSI: 2
[  244.820786] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  244.823169] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1037.464609] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX


christoph@server:~$ ls -l /dev/disk/by-id
insgesamt 0
lrwxrwxrwx 1 root root  9 Nov 12 22:22 ata-DV-18E -> ../../sr0
lrwxrwxrwx 1 root root  9 Nov 12 22:22 ata-ST940210A_5QX1YJTA -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 12 22:22 ata-ST940210A_5QX1YJTA-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 12 22:22 ata-ST940210A_5QX1YJTA-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov 12 22:22 ata-ST940210A_5QX1YJTA-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov 12 22:22 dm-name-server--vg-root -> ../../dm-0
lrwxrwxrwx 1 root root 10 Nov 12 22:22 dm-name-server--vg-swap_1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Nov 12 22:22 dm-uuid-LVM-sN1CMonSgtG4qdhof51BbYPvvVsShU3tKIyZjloxGzYSqQgvADz0mq6Cyh4sXv23 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Nov 12 22:22 dm-uuid-LVM-sN1CMonSgtG4qdhof51BbYPvvVsShU3tvNyJgsvzcvg8y00hGIRqohLntIPkrWri -> ../../dm-0
lrwxrwxrwx 1 root root  9 Nov 12 22:22 scsi-SATA_ST940210A_5QX1YJTA -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 12 22:22 scsi-SATA_ST940210A_5QX1YJTA-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 12 22:22 scsi-SATA_ST940210A_5QX1YJTA-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov 12 22:22 scsi-SATA_ST940210A_5QX1YJTA-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Nov 12 22:26 usb-XXXXXXXX_U168CONTROLLER-0:0 -> ../../sdb


christoph@server:~$ sudo dd if=/dev/zero of=/dev/sdb
dd: »/dev/sdb“ wird geöffnet: Kein Medium gefunden
christoph@server:~$ sudo shred /dev/sdb
shred: /dev/sdb: konnte nicht zum Schreiben geöffnet werden: Kein Medium gefunden

```

Now, can anybody tell me, how I might be able, to use my USB stick again. When using fdisk or parted it also does not work.

Would be so nice, if anybody could help me with that.

---

### Post by sudodus on 2014-11-13
Welcome to the Ubuntu Forums :-)

If you are running Ubuntu or another linux distro, you can install gparted from the repositories

```
sudo apt-get install gparted
```

and try to use gparted to create a partition table and a file system in a partition. It should work. If you cannot 'see' the pendrive, if you can 'see' it as for example /dev/sdb, but cannot create or edit the partition table or write to it (for example with dd, like you tried), I'm afraid that it is damaged.

Try to connect it to different USB ports in the computer, and if possible, try also with another computer, because some pendrives are not recognized properly by some motherboards.

You can try the corresponding operations with Windows or MacOS (to format the pendrive).

-o-

But it happens quite often that USB pendrives stop working. The lifetime (number of write operations) is shorter than that of hard disk drives. There is a programmable interface. That interface might be written to by mistake and damaged. I don't know how to write to (alias program) that interface, but I know that it exists. You can find information about it via the internet.

---

### Post by drpsy on 2014-11-14
Thanks, but isn't gparted just a GUI for parted which I already tried to use?

Anybody else an idea what might cause the Problem?

---

### Post by sudodus on 2014-11-14
> **drpsy said:**
> Thanks, but isn't gparted just a GUI for parted which I already tried to use?


Maybe the origin of it, but not exactly a GUI for parted. It is a program with its own features.

> Anybody else an idea what might cause the Problem?

I agree with the *drpsy*, please chip in with *your* tips! You may have a solution :-)

---

### Post by yancek on 2014-11-14
Which version of windows are you using to run the makeboot.bat file?  Did you follow the instructions for the Windows Method B on their site?

[http://gparted.org/liveusb.php](http://gparted.org/liveusb.php)

---

### Post by Vegan on 2014-11-15
I created a USB stick with Linux in Windows with the Linux Live USB tool and the stick is also allocated for persistent use so that I can update and and install additional packages

All you need is 8GB but I used a 32GB stick which has lots of room for disk tools etc

---

### Post by drpsy on 2014-11-16
I used Windows 8.1 64bit and followed the instructions. But is it even possible, that a program destroys an USB-stick?

---

### Post by sudodus on 2014-11-17
Yes, it is possible. But normal programs, that connect to the USB-stick with standard methods (of Windows, Linux, MacOS) will not destroy it. Such programs might destroy a file, a file system or a partition table, but that can be repaired or created again from the beginning. Only programs writing into the programmable interface 'behind the curtains' might change or destroy the pendrive (unless you have the special tools for repairing it).

On the other hand, an electric discharge, static electricity or a spark, can destroy a pendrive. And wear, repeated writing, will gradually destroy a USB-stick as well as a flash card.

If you want to know more, you can start with the following links

[https://en.wikipedia.org/wiki/Flash_memory](https://en.wikipedia.org/wiki/Flash_memory)

[This link to a post by DuckHook in the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426") describes how a flash drive works, and how it can fail, first getting read-only, then totally 'bricked'.

---

### Post by Farinet on 2015-01-12
Ceteris paribus, i have the same identical problem with the same stick. Only that mine "died" after changing something in the multisystem setup.I used it as multiple boot with different distros (cfr.  [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/) ).

I can see the stick in lsusb and with dmesg as well. Dmesg says:

--------
[62751.493696] usb 3-1: new high-speed USB device number 11 using xhci_hcd
[62751.609373] usb 3-1: New USB device found, idVendor=048d, idProduct=1168
[62751.609383] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[62751.610981] usb-storage 3-1:1.0: USB Mass Storage device detected
[62751.611116] scsi16 : usb-storage 3-1:1.0
[62752.614500] scsi 16:0:0:0: Direct-Access     XXXXXXXX U168CONTROLLER   0.00 PQ: 0 ANSI: 2
[62752.616392] sd 16:0:0:0: [sdb] Attached SCSI removable disk
----------

So, i'd be interested

a) if there is or was any solution here
b) if there are any linux tools which are able to format/repair/re-install (a possible mssing mbr or something) a usb stick.

Neither fdisk, nor (g)parted recognize the stick. It's my guess in the dark i should act some "layer" lower that those 2 programs to make the stick newly usable.

Thanks in advance for your patience!

---

### Post by sudodus on 2015-01-12
It may be or may not be the same problem. There might be hope for your pendrive, *Farinet*, because of the last line you show from dmesg:

```
[62752.616392] sd 16:0:0:0: [sdb] Attached SCSI removable disk
```

If it describes the pendrive (an not another USB device), and can identify it as /dev/sdb, you might be able to wipe the first megabyte with [mkusb]("https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device") and after that create a new partition table (and new partitions) with ***gparted***.

If it is read-only it might be gridlocked. [See this link and links from it]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297").

---

### Post by Farinet on 2015-01-12
> **sudodus said:**
> It may be or may not be the same problem. There might be hope for your pendrive, *Farinet*, because of the last line you show from dmesg:

```
[62752.616392] sd 16:0:0:0: [sdb] Attached SCSI removable disk
```

If it describes the pendrive (an not another USB device), and can identify it as /dev/sdb, you might be able to wipe the first megabyte with [mkusb]("https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device") and after that create a new partition table (and new partitions) with ***gparted***.

If it is read-only it might be gridlocked. [See this link and links from it]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297").

It describes the pendrive: yes! But it is *NOT* identified as /dev/sdb - that's the problem . . .

---

### Post by sudodus on 2015-01-12
Sometimes it works in one computer but not in another one, or in one USB  port but not another one - try in more than one computer, if you  haven't done that yet.

When a pendrive is not identified as a mass storage device (/dev/sda , /dev/sdb ...), I don't know any tool, that can recover it.

---

### Post by Farinet on 2015-01-13
I tried with lubuntu, aptosid, slackware and macos X- but to no extent. Mkusb sees the device but is unable to speak to it as /dev/sdb . Now, i know there is a cli tool called **usb_modeswitch** (which is made for other purposes, obviously). This tool **can** adress and manipulate the device, so my hope is, there might be anyway a way to access the stick. But unfortunately i'm not knowledged enough :-( (Otherwise, a strong magnet?? ;) ).

TIA for any pointer!

---

