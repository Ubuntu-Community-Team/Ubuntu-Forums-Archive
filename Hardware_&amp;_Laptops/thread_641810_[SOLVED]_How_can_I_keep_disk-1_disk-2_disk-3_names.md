---
title: "[SOLVED] How can I keep disk-1 disk-2 disk-3 names from changing?"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by gilf on 2007-12-15
I have a problem with the disk partition names changing practically every boot in Gutsy Ubuntu.

These partitions lie on a single external hard drive. One of the partitions has the Thunderbird mail folders on it.

As a result of the constant changing, I have to alter the path in Thunderbird's profile.ini file after practically every boot in order to access my mail.

I am not plugging in other hard drives or camera cards to cause these changes, usually.

Two of the external drive  partitions are reiserfs and one is a FAT32  The FAT32 has the Thunderbird mail files on it.

Is it possible to freeze these partition names through a UUID in fstab or someting? I thought this was already a feature of Gutsy....

---

### Post by rsambuca on 2007-12-15
Could you elaborate here?  When you say you change the path in the Thunderbird profile.ini for instance.  Does it work by /dev/... designations?  If the external is always connected, you can add it to your fstab, so it shouldn't change.

---

### Post by gilf on 2007-12-15
Thanks rsambuca,

The appropriate part of the profile.ini for thunderbird looks like this:

[Profile1]
Name=steve
IsRelative=0
Path=/media/disk-1/Thunderbird
Default=1

That "/media/disk-1 entry has to be changed to access the Thunderbird folder practically every boot.

Yes,  the external (usb) hard drive is always connected.

I just looked at /etc/fstab, and it isn't there. So that explains it.

Not quite sure how to enter it..

---

### Post by rsambuca on 2007-12-16
Try one of these two commands to see if it shows you the UUID.  Then I think you might be able to add it to the fstab (I have never added an external to the fstab before, but I think it should work).

```
blkid
```or

```
ls /dev/disk/by-uuid/ -alh
```

---

### Post by gilf on 2007-12-18
SOLVED:

I started to try to add entries to fstab, but it was unnecessary. After trying a few things I realized that nautilus can basically handle fstab graphically.

To assign a sticky name to a partition I found I could:

1.) On the desktop, open the "Disk-1" (or Disk-2" -- whatever) and verify that it opens the partition that I wanted to name as a Volume permanently.

2.) Back out of it to the desktop.

3.) Right click onthe disk icon.

4.) Select Properties

5.) Select the Volume tab [COLOR="Red"](I didn't select the disk tab -- I  wanted volumes -- important since my disk has partitions with a variety of filesystems -- selecting the disk tab and entering filesystem information would have made the system act as if  I only had one filesystem)[/COLOR]

6.)In the Volumes tab, click on the Settings "twistie" (small triangle) to open settings entry lines. 

7.)  I entered the mount point as Data-Disk, which was the sticky name I wanted for this partition. I didn't fill in the filesystem type or mount options -- these were shown correctly at the top of the window already.

8.) I rebooted to make the changes happen.

9.) I now had an Icon for "Data-Disk" on my desktop, and it is permanent. I've plugged and unplugged other USB devices, and rebooted to see if I could affect it, but this name is always properly associated with the partition I attached it to.

Now, to resolve the Thunderbird mail problem:

I opened /home/[COLOR="Blue"]steve[/COLOR]/.mozilla-thunderbird/profiles.ini and changed the path to:


[Profile1]
Name=[COLOR="Blue"]steve[/COLOR]
IsRelative=0
[COLOR="Red"]Path=/media/Data-Disk/Thunderbird[/COLOR]
Default=1

(substitute your username for [COLOR="Blue"]steve[/COLOR], and your own volume/mailfolder name for[COLOR="Red"] Data-Disk/Thunderbird[/COLOR] if you do this on your own system.


This resolved my problem  the constantly re-appearing Tthunderbird error message:

" Thunderbird is already running . . . "

---

