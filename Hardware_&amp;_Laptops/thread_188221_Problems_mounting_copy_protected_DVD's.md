---
title: "Problems mounting copy protected DVD's"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by Grue on 2006-06-03
I've just installed Ubuntu 6.06 on my brothers computer, since he was in awe after watching my install. Problem is, Ubuntu won't mount his Civ4 CD because of missing permissions. Cedega complains about this also in it's setup, but the fix provided doesn't work (chmodding hda with 644).

The computer automounts 'normal' DVDs/CDs without problems, but when I try to access the Civ4 CD it gives the error:
 "The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "cdrom"."

The Cedega error is:
```

A problem was detected with your CD/DVD-ROM devices.  Some or all copy protected games
may not work correctly with your drives.  Check the permissions on your CD/DVD-ROM device (in /dev). The device can be found in the /etc/fstab file.

In a terminal perform:

ls -la /dev/CDROM (where CDROM is the device for your system)

Make sure that all users have rx permissions.  If users do not have rx permissions then add the permissions by running

The device may be a symbolic link to a second device, for example:

lrwxrwxrwx  1 root root 3 Mar 23 05:50 /dev/cdrom -> hdc 

Here we can see that /dev/cdrom is a link to /dev/hdc.  Be sure to check permissions on the symbolically linked devices as well.

```

I'm really miffed about this, since he won't use Ubuntu/Linux if I can't get this up and running before tomorrow evening when he goes home...

I don't understand why fdisk -l doesn't list the two DVD drives, even when a CD is mounted, but maybe this is because it's handled by udev in a special way?

---

### Post by givré on 2006-06-04
Sorry for the delay man.
So, what do you have in your /etc/fstab /etc/mtab (when you have your cd in) and what is the result of ls -la /dev/hdc

---

### Post by ctschap on 2007-05-11
Looks like its been a while for this thread. Has a solution been found by anybody?

I tried the same thing a few days ago (encountering the same problem) and have been searching the forums ever since.

I am running Feisty. Normal CDs and DVDs automount without a problem. However, when I insert something like Civ4, SimCity 4, or the XP Pro install disk (trying to setup an XP VM) it won't read the disk.

---

### Post by Synnick on 2007-08-17
I agree with this post just moved from FC onto a new machine with Feisty but if all the permissions are this restrictive... and I don't have a clue how to sort them all I will have to move to another distro. Why can't permissions be easily set to enable access to the CD/DVD when they are protected? I can't even log into gnome as root to work around this. I really wanna see doom III on my new hardware but if reading the disk is this difficult I don't like my chances.

---

