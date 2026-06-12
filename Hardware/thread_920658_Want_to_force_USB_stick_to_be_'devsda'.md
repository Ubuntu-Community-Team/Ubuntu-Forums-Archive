---
title: "Want to force USB stick to be '/dev/sda'"
date: 2008-09-15
forum: Hardware
---

### Post by plonka2000 on 2008-09-15
Hi all,
I'm quite stuck trying to figure something out.

I'm trying to force my USB stick to be /dev/sda in my system before all my SATA drives (So that they can be whatever after that like sdb sdc etc) but I cant find a solid answer for how to get it done.

The reasoning behind this is because Ubuntu itself is installed onto the USB key and the internat SATA drives are used for a RAID5 volume. However, this volume will grow as more drives are added... And there lies my problem in that everytime a drive is added the USB mounting is pushed back.

I've googled and trauled the ubuntu forums but the 2 options I have come up with seemt to either edit my /boot/grub/device.map or another possible answer which is to use the devlabel tool, which I cant work out how to locate and install onto my system (Ubuntu Server 8.04 x64).

The only device I want to specify is my USB, which always ends up at the end of the disk mountings. It started off as /dev/sda but now its /dev/sdd and will keep being pushed back.

Can anyone provide help?

Thanks all.

---

### Post by bingoUV on 2008-09-15
Where do you mention the device name of the USB hard disk? I ask this to figure out why do you care about its device name changing? Do you mention it in /etc/fstab, or /boot/grub/menu.lst ? Or somewhere else?

In most places, UUID should work instead of the device name. The syntax of using UUID will be a bit different, but UUID of a device is stable and does not change by adding more drives to the system. To determine the UUID, do 
```

sudo blkid

```

---

### Post by plonka2000 on 2008-09-15
> **bingoUV said:**
> Where do you mention the device name of the USB hard disk? I ask this to figure out why do you care about its device name changing? Do you mention it in /etc/fstab, or /boot/grub/menu.lst ? Or somewhere else?

In most places, UUID should work instead of the device name. The syntax of using UUID will be a bit different, but UUID of a device is stable and does not change by adding more drives to the system. To determine the UUID, do 
```

sudo blkid

```

Thanks for replying, and I dont mean to sound negative but I dont think you read my first post properly.
I did the blkid and it gave me the UUID for my USB key as thats where ubuntu is installed, which is is all well and good.

The reason I care as to what assignment the USB key has is because UBUNTU is installed on the USB key.
When I installed the system all was well as the USB was the only drive and was recognised as **/dev/sda**. After everything was setup, I plugged in all my SATA drives for RAID (Shutdown first obviously). Subsequently, when I started back up my system, **/dev/sda** which is the USB key magically became **/dev/sdd**, which I dont want.

I just would like to find out how to force the system to recognise my USB key as **/dev/sda** by whatever means.

---

### Post by plonka2000 on 2008-09-15
Hi again,
I got a dump of my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=06f7a0fb-cb7c-4795-a299-493501a3a1bd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5d2adfc4-3a28-47a5-9e1b-7d1202dc52ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

is there a way I can use this to specify my mount points?

Thanks.

---

### Post by Whiffle on 2008-09-15
I think you're on the right track.  I think the first think I would try is doing it by UUID according to this howto:

[http://wiki.linuxquestions.org/wiki/Booting_from_USB#Use_a_unique_device_name](http://wiki.linuxquestions.org/wiki/Booting_from_USB#Use_a_unique_device_name)

---

### Post by bingoUV on 2008-09-16
> **plonka2000 said:**
> Thanks for replying, and I dont mean to sound negative but I dont think you read my first post properly.
I did the blkid and it gave me the UUID for my USB key as thats where ubuntu is installed, which is is all well and good.

The reason I care as to what assignment the USB key has is because UBUNTU is installed on the USB key.
When I installed the system all was well as the USB was the only drive and was recognised as **/dev/sda**. After everything was setup, I plugged in all my SATA drives for RAID (Shutdown first obviously). Subsequently, when I started back up my system, **/dev/sda** which is the USB key magically became **/dev/sdd**, which I dont want.

I just would like to find out how to force the system to recognise my USB key as **/dev/sda** by whatever means.

Sorry, I tried to read your post but could not find a good reason why you would want the device name of the USB hard disk to be /dev/sda. Emotional attachment of the hard disk with device name ;) ?

Looking at your fstab, it will not cause any trouble whether the device name is /dev/sdd, or any other. I don't know if this helps, but one thing that is reliable is that /dev/disk/by-uuid/06f7a0fb-cb7c-4795-a299-493501a3a1bd will be a symbolic link that will always point to the device that your / partition is mounted with.

---

### Post by plonka2000 on 2008-09-16
> **bingoUV said:**
> Sorry, I tried to read your post but could not find a good reason why you would want the device name of the USB hard disk to be /dev/sda. Emotional attachment of the hard disk with device name ;) ?

Looking at your fstab, it will not cause any trouble whether the device name is /dev/sdd, or any other. I don't know if this helps, but one thing that is reliable is that /dev/disk/by-uuid/06f7a0fb-cb7c-4795-a299-493501a3a1bd will be a symbolic link that will always point to the device that your / partition is mounted with.

I kind of came to this same conclusion yesterday and just ran with it. So far all seems fine and I got my SATA RAID 5 (Thinking of going with RAID 6 though, as I will be adding more drives soon and I'm paranoid anyway).

However, I'm having a really annoying issue with Samba.
I've created a public share and for some reason I can access it from my Windows PC, but I cant write to it, even though I'm sure I've added all the correct permissions to this share.

IS it going to be something to do with my local permissions?
Btw, the share is located on my newly formed RAID5.

Thanks.

---

### Post by ghostis on 2011-01-18
Use a local udev rule to detect the USB stick's serial number and assign a device file to it (e.g. "sda"). The device filename is arbitrary, so it may make sense to use something more meaningful than "sda".

See: [http://www.wains.be/index.php/2010/04/10/udev-always-the-same-device-name-for-your-usb-drives/]("http://www.wains.be/index.php/2010/04/10/udev-always-the-same-device-name-for-your-usb-drives/")

and

[http://ubuntuforums.org/showthread.php?t=168221]("http://ubuntuforums.org/showthread.php?t=168221")

For a canonical reference, see: [http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html")

---

