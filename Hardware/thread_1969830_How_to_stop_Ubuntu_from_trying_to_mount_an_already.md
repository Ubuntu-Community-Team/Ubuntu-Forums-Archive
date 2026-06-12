---
title: "How to stop Ubuntu from trying to mount an already mounted device."
date: 2012-04-30
forum: Hardware
---

### Post by TLangas on 2012-04-30
I am having an interesting issue, on multiple Ubuntu installations, regarding external drives. Not all installations.

Example:
I have a Ubuntu 10.04 to 11.10 Server Edition, with a gui desktop installed (ubuntu-desktop). One external hard drive is connected and mounted through /etc/fstab, using it's uuid and mounted to /media/xhd1.
My issue arises after a week or two. I am no longer able to read or write to the external drive.
When viewing the "Places" menu, the drive appears twice.
The mount command shows the device is /dev/sdc, but blkid says it is /dev/sdd.
Unmounting and remounting, or rebooting, will temporarily fix the issue.

If I am currently logged in, I get a error message, along the lines of "device is already mounted". Sorry, I forgot to write down the actual error. 

As I am trying to push one of my system backups to the external, I don't like the idea of it failing, due to Ubuntu trying to mount the same device more than once.

Has anyone seen this issue before? Are there any suggestions, to help find out what is actually causing this issue?

I will be able to collect more information the next time this issue occurs.

---

### Post by ahallubuntu on 2012-04-30
Any chance you have two partitions with the same UUID on your system, including any of the partitions on your external drive?

---

### Post by TLangas on 2012-04-30
It is a new hard drive, with one large partition.

blkid:
/dev/sdd1: LABEL="xhd1" UUID="e23ce182-2102-4662-8817-d4ec9826716f" SEC_TYPE="ext2" TYPE="ext3"

mount:
/dev/sdc1 on /media/xhd1 type ext3 (rw)

/etc/fstab:
UUID=e23ce182-2102-4662-8817-d4ec9826716f /media/xhd1    ext3    defaults     0 0


When the issue occurs feels completely random. from 1 week to 1 month or longer.

BTW, I was under the assumption, that uuid stood for Universal Unique Identifier, so there should only be one hard drive with that identifier. Also, it is the only external device connected. Each installation would have it's own external hard drive.

Edit: By each installation, I mean different computer.

---

### Post by ahallubuntu on 2012-04-30
You aren't SUPPOSED to have more than one UUID per system, but it's completely possible to duplicate a partition using the same UUID (inadvertently) and have two of the same attached at the same time.  For example, if you clone a hard drive or partition to another drive (making a crude backup with the dd command for example) you could have two different partitions with the same UUID.  It's a good idea to change one of them (you can do it using the tune2fs command).

Obviously you need to figure out why this device is showing up as both sdc and sdd .  

FYI, I wouldn't use /media to mount devices in fstab.  Use /mnt instead and leave /media to Nautilus to use for manually-mounted devices.  Consider changing that in your /etc/fstab and rebooting and see how things look.

---

### Post by CharlesA on 2012-04-30
Note: Mounting in /media causes the drive to show up in places as well. Mount it elsewhere.

---

### Post by TLangas on 2012-04-30
Thanks for explaining that. I forgot about the DD command.

I'll change the mount location out of media and see if the error reappears. Thanks for the suggestion.

---

