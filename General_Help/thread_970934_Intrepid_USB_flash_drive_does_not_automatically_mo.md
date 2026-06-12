---
title: "Intrepid: USB flash drive does not automatically mount"
date: 2008-11-04
forum: General Help
---

### Post by lian1238 on 2008-11-04
Inserting a USB flash drive gives two errors:
The first:
**Cannot mount volume.**
Invalid mount option when attempting to mount the volume 'LIAN'.

The second:
**Unable to mount LIAN**
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

dmesg gives this upon insertion:
```

[ 2104.188156] usb 5-2: new high speed USB device using ehci_hcd and address 6
[ 2104.324537] usb 5-2: configuration #1 chosen from 1 choice
[ 2104.327564] scsi3 : SCSI emulation for USB Mass Storage devices
[ 2104.329049] usb-storage: device found at 6
[ 2104.329066] usb-storage: waiting for device to settle before scanning
[ 2109.328336] usb-storage: device scan complete
[ 2109.331267] scsi 3:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2109.334789] sd 3:0:0:0: [sdb] 1952256 512-byte hardware sectors (1000 MB)
[ 2109.335807] sd 3:0:0:0: [sdb] Write Protect is off
[ 2109.335821] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2109.335827] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 2109.337915] sd 3:0:0:0: [sdb] 1952256 512-byte hardware sectors (1000 MB)
[ 2109.338917] sd 3:0:0:0: [sdb] Write Protect is off
[ 2109.338929] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2109.338933] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 2109.339808]  sdb: sdb1
[ 2109.342077] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 2109.343062] sd 3:0:0:0: Attached scsi generic sg2 type 0

```

I can manually mount the drive with the command:
```
sudo mount /dev/sdb1 /media/disk/
```

---

### Post by flashgc on 2008-11-04
Thanks for that....

But what about the server version that doesn't try to mount automatically?

I used lshw with and without the flash drive plugged in and the difference was:
```
*-scsi
       physical id: 1
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage
```
How would we mount this puppy?

---

### Post by lian1238 on 2008-11-06
Bump on invaild mount option?

---

### Post by pnavarrc on 2008-11-06
Hello,

   I have the same problem. I can mount the device (a usb key) manually, but is not mounted automaticaly. Other devices (external hard disk, my cell phone) are recognized and mounted without problems.

      Pablo.

---

### Post by lian1238 on 2008-11-06
Do you get the same output in dmesg?

Was that your first post? Welcome to the forums.

---

### Post by nemarona on 2008-11-12
Before this dies out...

I'm having the same problem. I upgraded from Xubuntu 8.04 recently, and now usb drives don't get automatically mounted when inserted. Manually mounting works.

A guess: Might this be related with Xubuntu now naming HDD partitions sda, sdb, etc instead of the older hda, hdb? USB drives have always been named "sda".

---

### Post by TWO on 2008-11-23
Up until about 10 minutes ago I had the problem of being unable to access my phone memory or USB memory sticks.  After some proper googling, I came across the following thread:

[http://backports.ubuntuforums.com/showthread.php?t=731223](http://backports.ubuntuforums.com/showthread.php?t=731223)

For me (and for the user of that thread) happened to have installed Ubuntu by the USB method and for some reason fstab creates an entry for the USB medium that is used. 

More info can be found in Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150872](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150872)

Anyway, that causes problems for the whole automatic booting feature. 

IN my case, the problem lied with an 'sdb1' entry in my etc/fstab file. Once I deleted that entry and rebooted, hey presto, I can access my phone memory!

Problem solved! :-D

---

### Post by lian1238 on 2008-11-30
I didn't install by USB.

Although, i have the following line in /etc/fstab for VBox USB support to work.
```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

---

### Post by Rohaq on 2008-12-07
> **TWO said:**
> Up until about 10 minutes ago I had the problem of being unable to access my phone memory or USB memory sticks.  After some proper googling, I came across the following thread:

[http://backports.ubuntuforums.com/showthread.php?t=731223](http://backports.ubuntuforums.com/showthread.php?t=731223)

For me (and for the user of that thread) happened to have installed Ubuntu by the USB method and for some reason fstab creates an entry for the USB medium that is used. 

More info can be found in Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150872](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150872)

Anyway, that causes problems for the whole automatic booting feature. 

IN my case, the problem lied with an 'sdb1' entry in my etc/fstab file. Once I deleted that entry and rebooted, hey presto, I can access my phone memory!

Problem solved! :-D

Just want to confirm that this was the problem for me, having installed via USB on my Acer Aspire One. Commented out that line, and I'm mounting to my heart's content!

---

### Post by naijadev on 2008-12-15
Has anyone solved the problem? Am having the same problem since I upgraded from 8.04. I upgraded via the alternate cd. Manual mounts works.

---

### Post by lian1238 on 2008-12-24
Still no fix?

---

### Post by Hopalong on 2008-12-26
I have two USB sticks, maker LG,512 MB. One mounts automatically on insertion: the other does not. In Windows Vista (dual booted) both sticks work and can be written and read.
  What does Windows have that Ubuntu hasn't? Or alternatively, what has been done to one stick to make it unusable in Ubuntu, 8.04.

---

### Post by ju2wheels on 2008-12-26
One of the other things that can cause usb drives to not be able to boot, especially on netbooks is having a line for the cdrom in fstab but not actually having a physical cdrom drive on your pc.

For example, my desktop (which does have a cdrom) has this as a line in /etc/fstab:
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

If you are using a netbook or pc with no cdrom drive, you will want to put a '#' character at the beginning of the line to comment it out and disable it so it doesnt interfere with automounting drives.

In addition, for those that have said that your usb drives auto mount on Windows but not Linux, be aware that after using them on Windows, DO NOT just pull the usb drive out. Go the usb options by the clock and safely release the usb device before physically detaching it from your machine. This is especially important if the file system on it is NTFS. If you fail to do this, then you will have to force mount it once on Linux in order for it to work. It should then automount the next time it is inserted as long as you always remember to properly unmount it before removing it.

```

sudo mount.ntfs-3g -o force /dev/sdb1 /media/somefolder

```

If you are still having issues, some of you may want to just post your /etc/fstab config as it might be the source of the issue for some of you.

---

### Post by Hopalong on 2009-01-01
The answer to my question is the ability to read USB's formatted as exFAT (a new format by you know who). See my post 'USB's not auto-mounting' in this forum.

---

### Post by Dilligaf on 2009-01-04
I had the same output from dmesg as the original poster when inserting a 8 gig flash drive, what I found is that if you go into gparted and turn off the boot flag on the drive it will automount without any problems. Let me know if this helps you.

Mike

---

### Post by lian1238 on 2009-01-04
> **Dilligaf said:**
> I had the same output from dmesg as the original poster when inserting a 8 gig flash drive, what I found is that if you go into gparted and turn off the boot flag on the drive it will automount without any problems. Let me know if this helps you.

Mike

I turned off the boot flag, but the problem persists. Is yours FAT32? If I format it to ext2 or ext3, it mounts fine. It doesn't mount if it's FAT32 or FAT16.

I've created a bunch of scripts to make the mounting go faster.
E.g. mount, unmount, run nautilus as root, change owner back to me.

Oh, how I envy you!

---

### Post by Dilligaf on 2009-01-05
My flash drive is Fat32. I don't know why the boot flag makes a difference but it worked for me. Sorry it doesn't work for you.

Mike

---

