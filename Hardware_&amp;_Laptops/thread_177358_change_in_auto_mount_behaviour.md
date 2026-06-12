---
title: "change in auto mount behaviour?"
date: 2006-05-16
forum: Hardware &amp; Laptops
---

### Post by handaxe on 2006-05-16
Hi,

Has anyone else experienced Dapper not auto-mounting ALL partitions of an external USB drive since updates around Thurs/Fri last week?

This for me is a new behaviour - as before all 3 partitions (ntfs, ext3, reiserfs) auto-mounted fine.

I know some folk have had problems getting a drive to auto mount at all but my issue is different. Not a show stopper as I can mount them manually.

Ta for info if any...

HA

---

### Post by darkvad0r on 2006-05-16
I have 2 external usb drives with 2 partitions each (sda1:ntfs, sda2:fat32, sdb1:hfs+, sdb2:fat32)  attached to a usb hub, the discs never seem to get mounted correctly (half of the times I can't access to the ntfs volume if not in root and the other half the hfs+ volume doesn't get mounted but the ntfs works fine)
I think it's because they change from sda to sdb and viceversa on boot (possibly an issue with the hub) making the entries in /etc/fstab incorrect. Maybe you have the same problem?

EDIT: sorry, I misread your post, but anyways, I'll leave my comment, maybe someone knows what I can do about it :)

---

### Post by handaxe on 2006-05-16
Hi,

Thanks.. I keep plugging in to the same usb port and the mount points are (or at least when it did it automatically, WERE) stable.

I can probably sort this my making fstab entries but wondered if this is a bug..

HA

[quote=darkvad0r]I have 2 external usb drives with 2 partitions each (sda1:ntfs, sda2:fat32, sdb1:hfs+, sdb2:fat32)  attached to a usb hub, the discs never seem to get mounted correctly (half of the times I can't access to the ntfs volume if not in root and the other half the hfs+ volume doesn't get mounted but the ntfs works fine)
I think it's because they change from sda to sdb and viceversa on boot (possibly an issue with the hub) making the entries in /etc/fstab incorrect. Maybe you have the same problem?[/quote]

---

### Post by thasheep on 2006-05-16
[QUOTE=handaxe]Hi,

Has anyone else experienced Dapper not auto-mounting ALL partitions of an external USB drive since updates around Thurs/Fri last week?

This for me is a new behaviour - as before all 3 partitions (ntfs, ext3, reiserfs) auto-mounted fine.

I know some folk have had problems getting a drive to auto mount at all but my issue is different. Not a show stopper as I can mount them manually.

Ta for info if any...

HA[/QUOTE]
Just noticed it then. I plugged in my mp3 player (only one partition) and it won't automount. I'm not sure when this change happened but it used to work under dapper. Manual mounting works fine.

---

### Post by handaxe on 2006-05-16
I suppose these issues could be inter-linked but I have the first partition auto-mounting but not the rest, which used to.

HA

[quote=thasheep]Just noticed it then. I plugged in my mp3 player (only one partition) and it won't automount. I'm not sure when this change happened but it used to work under dapper. Manual mounting works fine.[/quote]

---

### Post by thasheep on 2006-05-16
[QUOTE=handaxe]I suppose these issues could be inter-linked but I have the first partition auto-mounting but not the rest, which used to.

HA[/QUOTE]
Sorry, I just realised my problem was caused by a custom kernel - probably not worth reporting.

---

### Post by handaxe on 2006-05-17
For what it is worth - automounting problem solved by deleting /media/usbdisk and /media/usbdisk-1 mount points. Dapper now sees and automounts all 3 partitions.

HA

---

### Post by WelterPelter on 2006-05-17
My automount of a usb drive was working fine until this week. Now... nothing.

---

### Post by PapaWiskas on 2006-05-30
OK here is what I did to fix my issue.
This is all taken from my history in synaptic....keep in mind, I am not an expert, but I did fix my problem after reading and trying a bunch of stuff on automounting that did not work....so I did this myself, now my USB and CDROMS/DVDS automount fine and show icons on the desktop.

Here is the first thing I did...

Completely removed the following packages:
hal

Removed the following packages:
gnome-power-manager
gnome-session
hal-device-manager
hwdb-client

Then I did the following...
Installed the following packages:
gnome-power-manager (2.14.3-0ubuntu11)
gnome-session (2.14.1-0ubuntu11)
gnome-utils (2.14.0-0ubuntu5)
gnome-volume-manager (1.5.15-0ubuntu10)
hal (0.5.7-1ubuntu1
hal-device-manager (0.5.7-1ubuntu1
hwdb-client (0.6-0ubuntu10)

And now everything works again, dont ask me how or why because I dont know.

---

### Post by dmalinovsky on 2006-06-01
Pity, but it didn't work for me.  I tried to do as stated in [this wiki page]("https://wiki.ubuntu.com/DebuggingRemovableDevices"), but gnome-volume-manager even didn't start for me! I tried to run it with "strace" command, but didn't find any clues...

---

### Post by spyrakos on 2006-06-01
Same problem here. Everything worked fine until a couple of days ago. Ever since (and some 30-40 updates applied automatically), I'm not allowed to mount removable drives anymore, with system telling me only root can mount them; since it is my understanding that root login is not available in ubuntu, I guess I'll just have to manually mount and unount them every time? Oh boy, this sucks...:confused:

---

### Post by dmalinovsky on 2006-06-01
My problem is slightly different.  I have no automounting, but if I go to Places/Computer and hit on cdrom icon, it's get mounted and I see the icon on my Desktop.  I also can eject the CD without any problem.

---

### Post by daveg on 2006-06-28
[QUOTE=dmalinovsky]My problem is slightly different.  I have no automounting, but if I go to Places/Computer and hit on cdrom icon, it's get mounted and I see the icon on my Desktop.  I also can eject the CD without any problem.[/QUOTE]
I'm getting that problem as well. Its most annoying :confused:

---

### Post by kurbacik on 2006-06-28
I have a quirky problem: when I connect my digital camera through usb cable to my laptop, automount works on the usb port on the right side of my laptop, while it doesn't work at all (not even manaul mounting) for the two usb ports on the left hand side. This behavior is new to me, I've never had this problem previously with Dapper and with Breezy. Does anybody have a similar problem?

---

### Post by dmalinovsky on 2006-06-28
[QUOTE=daveg]I'm getting that problem as well. Its most annoying :confused:[/QUOTE]
I filed [appopriate bug]("https://launchpad.net/distros/ubuntu/+source/gnome-volume-manager/+bug/49666") into Ubuntu bug tracker, maybe developers will answer it.

---

### Post by drycellbattery on 2006-08-01
Same problem, I have all the latest gnome, hal and hwdb-client packages

---

### Post by drycellbattery on 2006-08-09
I took a look in my /etc/fstab and saw all the partitions (/dev/sda1-4) in there so I deleted those entries and rebooted. I plugged my usb drive back in and it automounted. I guess this happened from installing Ubuntu with my drive turned on.

---

### Post by xinelo on 2006-08-09
please ignore this post

---

