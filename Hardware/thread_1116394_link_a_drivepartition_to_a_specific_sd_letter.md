---
title: "link a drive/partition to a specific sd letter"
date: 2009-04-04
forum: Hardware
---

### Post by KerryLB on 2009-04-04
Is there any way I can tell Ubuntu to use a certain sd letter to 'refer to' a specific drive?  i.e. what I want to do, is to make sure that whenever I plug in my first external drive (lets call it MyDisk1), to use sdc1,sdc2,etc to refer to the drive's partitions, even though sdb may be available to use, and whenever I plug in MyDisk2, to use sde1,sde2,etc.

I have the partitions for all my external drives/flash disks set up in fstab, but sometimes things get 'mixed up' depending on what order I connect the drives.

---

### Post by CyberMando on 2009-04-06
Googleing "udev persistent usb drive" pulled up a number of hits including this one which looks pretty straight forward.
[http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-8-sect-10.html]("http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-8-sect-10.html")

---

### Post by drs305 on 2009-04-06
> **KerryLB said:**
> I have the partitions for all my external drives/flash disks set up in fstab, but sometimes things get 'mixed up' depending on what order I connect the drives.

If you are going to go that route, you can replace the fstab "sdXX" designation with the UUID or a label name. To get the label name, run either of these:
```

sudo blkid
ls -al /dev/disk/by-uuid/

```

Example:
/dev/sda3 /media/mydata ext3 defaults 0 2
UUID=09d5d9e5-1f57-45a2-a930-395107a5dd65 /media/mydata ext3 defaults  0 2
LABEL=mydata  /media/mydata  ext3  defaults   0 2

---

### Post by KerryLB on 2009-04-06
Thank you CyberMando and drs305

The link CyberMando gave me explained what I need to know.  It also pointed right back to a HowTo on ubuntuforums, which I must have missed in my search... :
[HOW TO: Make static mountpoint/devicename for usb hddrive]("http://ubuntuforums.org/showthread.php?t=91948")

The only problem with these two articles, is that where it says:
BUS=="usb", SYSFS{serial}=="6R0000065086", NAME{all_partitions}=="temp"
- the NAME section should only have one '=', so it would become:
BUS=="usb", SYSFS{serial}=="6R0000065086", NAME{all_partitions}="temp"

drs305, thanks for the info, but it looks a little confusing to little me:)  I think now I should be able to refer to my devices in fstab as '/dev/seagate3, /dev/XDcard1, etc etc' - am I right?

Thanks again guys, this is going to put an end to a lot of frustration!

---

### Post by CyberMando on 2009-04-06
This is interesting. I am running Jaunty and after I posted the likns I tried to use them, only to find that Jaunty has anew version of udev and udevinfo is no longer part of udev. Instead it uses udevadm. After messing with it for a few hours I ended up doing what drs305 suggested except that to get the device I used
sudo udevadm info --query=all --name /dev/sdc

---

### Post by KerryLB on 2009-04-06
Both udevinfo and udevadm work on Intrepid.

Actually, after my last post I realised my udev command was causing the system to create 'links' from freeagent1 right up to freeagent15 when I plug in the drive (even though that drive only has four partitions. My fault: I had misinterpreted the purpose of the '{all_partitions}' option.

Anyway, after more googling I got it to work the way I want it to.

Here's what's in /etc/udev/rules.d/10-local.rules:
> 
# seagate freeagent go
SUBSYSTEM=="block", SUBSYSTEMS=="usb", ATTRS{manufacturer}=="Seagate", ATTRS{product}=="FreeAgent Go", NAME="freeagent%n"


and here's the relevant section in /etc/fstab:
> 
/dev/freeagent2	/drives/Ext_Files	ntfs	auto,user,exec,rw
/dev/freeagent3	/drives/Ext_Multimedia	ntfs	auto,user,exec,rw
/dev/freeagent4	/drives/Linux_Files	ext3	auto,user,exec,rw


1. The partitions mount perfectly from fstab into the correct directories when I boot up.
2. Only the partitions that actually exist are listed in /dev (freeagent, freeagent1, freeagent2, freeagent3 and freeagent4),
...everything's working perfectly...I love Ubuntu! :D

---

