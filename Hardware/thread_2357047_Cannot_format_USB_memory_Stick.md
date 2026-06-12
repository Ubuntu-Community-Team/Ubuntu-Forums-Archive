---
title: "Cannot format USB memory Stick"
date: 2017-03-29
forum: Hardware
---

### Post by vangend.robert on 2017-03-29
I have several 32GB memory sticks (about 6). They came to me through regular software maintenance upgrades from AutoDesk. We have upgraded all our installations and it is highly unlikely that I will ever need to install this software from the sticks again since the software is also downloadable, I have the same software (pre-installed) on hard disk, and we are already two version further down the line.

I would like to re-purpose these flash drives, since it seems a waste just to throw them away or not use them anymore.

The problem is that they are read only and I cannot format / re-partition them.

I have tried several options:

1.) There is no external hardware switch, so I cannot change anything here.

2.) sudo hdparm -r0 /dev/sdf

         /dev/sdf:
         setting readonly to 0 (off)
         readonly      =  0 (off)
         
3.) sudo dd if=/dev/null of=/dev/sdf

         dd: opening `/dev/sdf': Read-only file system


4.) output from dmesg

[128062.008020] usb 2-1: new high-speed USB device number 3 using ehci_hcd[128062.141789] usb 2-1: New USB device found, idVendor=0930, idProduct=1400
[128062.141793] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[128062.141797] usb 2-1: Product: TOSHIBA USB DRV
[128062.141801] usb 2-1: Manufacturer: TOSHIBA
[128062.141804] usb 2-1: SerialNumber: 07085437761B9F71
[128062.273015] Initializing USB Mass Storage driver...
[128062.273162] scsi8 : usb-storage 2-1:1.0
[128062.273257] usbcore: registered new interface driver usb-storage
[128062.273260] USB Mass Storage support registered.
[128063.272929] scsi 8:0:0:0: Direct-Access     TOSHIBA  TOSHIBA USB DRV  PMAP PQ: 0 ANSI: 6
[128063.273599] sd 8:0:0:0: Attached scsi generic sg7 type 0
[128063.275539] sd 8:0:0:0: [sdf] 60566016 512-byte logical blocks: (31.0 GB/28.8 GiB)
**[128063.276095] sd 8:0:0:0: [sdf] Write Protect is on**
[128063.276100] sd 8:0:0:0: [sdf] Mode Sense: 2b 00 80 08
[128063.276542] sd 8:0:0:0: [sdf] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[128063.336813]  sdf: sdf1
[128063.339545] sd 8:0:0:0: [sdf] Attached SCSI removable disk

Even after hdparm -r0 /dev/sdf

5.) sudo fdisk /dev/sdf
administrator@dataserver:~$ sudo fdisk /dev/sdf
[U][B]
You will not be able to write the partition table.[/B][/U]


Command (m for help): d
Selected partition 1


Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1):
Using default value 1
First sector (2048-60566015, default 2048):
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-60566015, default 60566015):
Using default value 60566015


Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 87
Changed system type of partition 1 to 87 (NTFS volume set)


Command (m for help): w
_**fdisk: unable to write /dev/sdf: Bad file descriptor**_

6.) I am ruling out the possibility to physical damage, since all the drives are behaving exactly the same way.

7.) I have (under windows) found some utilities that allowed me to format the drives, and even write some data to them.. However, them minute I remove from the machine and put them back in the same machine, I see the directory I created, but the drive is read only again. The original OEM software is gone, and my directory is there, but it is no longer writeable.
8.) I have also seen several forums where various tools are suggested (Formatter, Phison_MPALL, Repair_v2.9.1.1, Restore v3.17.0.0, Killdisk, HDDLLF.4.40) , and several more I think.

I am at a loss now. Does anyone have any ideas or suggestions?

Thanks
Rob

---

### Post by Bucky Ball on 2017-03-29
You don't say which release of Ubuntu you are using. Please confirm. For some reason you are trying to do this in a terminal, so perhaps it is a server. Anyway ...

Do this with Gparted. It is in the repositories so just install. Launch Gparted and locate the USB via the drop-down in the top right-hand corner of the Gparted window. Right click any partitions and unmount them (they may be already unmounted or the 'mount' option is greyed-out; that is fine, go ahead).

Go to 'Device> Create partition table'. This will remove all partitions and data on the USB leaving free space. Apply.

When complete, right click the free space and partition/format how you want.

---

### Post by vangend.robert on 2017-03-29
Hello Bucky,

I am using Ubuntu 14.04, and yes it is a terminal, and yes it is a server. However, I did not mention in my earlier post that I have also tried with GParted on a live CD using my laptop. No luck here either. Still complains that the USB drive is read only.

I have been reading some other forums "http://whatrevitwants.blogspot.co.za/2011/06/repurposing-autodesk-usb-media_20.html", and it seems that it is required to flash the USB drive. The new challenge is to establish exactly which version of IC is on the drive, and then flash the drive correctly.

---

### Post by sudodus on 2017-03-29
Your description of failed commands makes me think that your USB memory sticks might be gridlocked, which is a read-only state in the beginning of the failing process. But it is also possible, that they can work some other way or that maybe only one or a few are damaged, and some of them can work.

***When a pendrive or memory card is read-only***
[LIST]
[*]On some pendrives and on many memory cards there is a small mechanical switch for write protection, that can toggle between read/write and read-only. You might have set it read-only without intention. (You already know this is not the case, but other people might be helped by this item.)
[*]Reboot the computer and try again to wipe the first megabyte with [mkusb](https://help.ubuntu.com/community/mkusb/wipe).
[*]Disconnect other USB devices. Sometimes USB devices can disturb the function for each other.
[*]Try other USB ports and another computer.
[*]Try another operating system (Windows, MacOS) in another computer.
[*]If you still cannot wipe the first megabyte of the drive, and the drive is read-only, it is 'gridlocked', and the next stage is that it will be completely 'bricked'.[/LIST]

```
sudo dd if=/dev/null of=/dev/sdf

dd: opening `/dev/sdf': Read-only file system
```

is not correct. You should use /dev/zero to generate zero-bytes:

```
sudo dd if=/dev/zero of=/dev/sdf

dd: opening `/dev/sdf': Read-only file system
```

but it is ***safer to use mkusb***, which wraps a safety belt around dd. mkusb helps you identify the target drive and provides a final checkpoint, to help you write the zeros to the correct drive. mkusb version 12 works also in text mode with 'dialog' text mode menus (see the first screenshot), so you can use it in Ubuntu Server. You can also use mkusb-nox with a simpler command line interface.

Furthermore, it is usually enough to write zeros to the first megabyte. After that you can use a partitioning tool to create a new partition table and file system(s). You can also use mkusb to restore to a standard storage device directly (see the second screenshot; there is a corresponding text mode menu).

See the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)
[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")
[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

