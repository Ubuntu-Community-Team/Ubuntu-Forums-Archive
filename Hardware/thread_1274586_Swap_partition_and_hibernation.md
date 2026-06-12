---
title: "Swap partition and hibernation"
date: 2009-09-24
forum: Hardware
---

### Post by David_jcd on 2009-09-24
Hello!
I know theer are tons of posts about swap partitions and swap files, but despite the searches i did, I couldn't solve my problem (sorry)...
I installed Ubuntu a couple of days ago, and I noticed my swap partition is only 628mb large.
I read that it doesn't matter (i have 2 Gb RAM), if I don't hibernate.
The problem is that I actually _want_ to hibernate! I read also that hybernation cannot use Swap files, but only swap partition, can anybody tell me what I have to do?

This is my HD:
[http://img196.imageshack.us/img196/5791/schermatae.png]("http://img196.imageshack.us/img196/5791/schermatae.png")

---

### Post by FuturePusher on 2009-09-24
Hmm.. You have a bit of an "awkward" partitioning on that disk, with Your root ("/") partition last... I'm not saying it's necessarily bad though!
"Linux OS:s work in mysterious ways..." :)

My suggestion is that You boot Your system up with a Ubuntu CD/DVD, and from there (**"commit"** the below steps **step-by-step**!):

* Step 1: Run gparted to resize Your "/" partition ("/dev/sda5") down to around  9 GB...
* Step 2: REMOVE the "sda6" partition (Your current swap partition)! (You may need to deactivate swapping on it first. If so, right-click it to do that...)
* Step 3: You'll now have nothing but free space after "sda5" ("/" partition)... Create A NEW swap partition there! Allocate all the space You can to it... (should be over 2 GB's).
* Verify that the new swap partition has the "sda6" partition designation, if it doesn't You may have to re-edit Your */etc/fstab* to reflect the change.

--- (The below assumes Your NEW partition is still designated "sda6", if it isn't, replace occurrences below with what it now is.) ---

* Run this in a terminal (no quotes!): "sudo blkid -g /dev/sda6" (updates things gparted may not take care of)
* Run this in "Run" dialog (press "Alt+F2" in Gnome): "gksudo gedit"... and then open the file "/boot/grub/menu.lst" there... and add the below to the end of each line, around the bottom of the file, starting with "kernel ..." (without the quotes, and with a preceeding space!):
"resume=/dev/sda6"


Now reboot Your system, and You should both have a larger "ordinary" swapspace... AND plenty of room for hibernation data on it, as well as Your kernel properly instructed from where to look for, and resume from, any earlier saved hibernation data.


Just a sidenote:
I've read that it **IS** technically possible to hibernate to, and resume from, swap **files**... but that setting that up is to cumbersome to be worth it, unless You have REALLY special needs for just that.
A swap partition, with space enough to hold the necessary contents of Your RAM memory, is the most convenient way to go.
I actually have one separate swap partition for hibernation, one smaller default only for regular swapping, and additional swap files for additional and on-demand system swapping... "overkill" for most users really.

Good luck with it! :)

---

### Post by David_jcd on 2009-09-25
Thank you, but somthing must have gone wrong: I can't boot anymore!
After selecting the OS, I get this message:

Boot from (hd0,4) ext3 [...]
Error 11 Unrecognised device string.

If there is a simple way to solve, i'll try it, but elsewhise, i think it's better to reinstall the whole OS on another position on the disc.
Do you think that moving the ubuntu partition to the left will ingrease reading speed?

---

### Post by FuturePusher on 2009-09-25
Sorry to hear something went wrong there...


I'm strongly suspecting You have the "GRUB" boot-sector loader on the NTFS formatted partiton "sda3", right? (You have the "boot" flag set on that partition, so that's where the computer tries to load an OS from at startup..)

Regarding higher speed at different locations of the disk: if I remember correctly, the best throughput is farthest to the "left", and the slowest farthest to the "right" (in graphical representations of a disk)... so Your NTFS partitions are the "fastest".

Unfortunately, one can't move around partitions as conveniently as one would like... it either takes some serious planning in advance, or just accepting a slightly less than optimal setup.


**I think the absolutely easiest & quickest way You can do this, now with You already prepared to reinstall Ubuntu, is to:**

* Use a bootable Ubuntu Live-CD/DVD (do a full "Try Ubuntu..." boot with it) to access Your old "/" partition from there... Purpose: to backup any personal documents/data You may already have stored.

* Delete the old Linux partitions with "gparted" (press "Alt+F2" and type in "gksudo gparted" to run the Gnome Partition Editor, when You're "in" the Live-CD...)
 (You should keep the "Extended" as it's a "holder" for partitions, and already conveniently sized... so just delete "sda5" & "sda6"!)

* Re-install Ubuntu in pretty much the exact same way You did previously, except this time: let the "/" ("root") partition take up 10GB, leaving the rest for the swap partition.
 (I suggest You still use the ext3 filesystem, it's solid, safe & fast once tuned a bit...)

The benefit of doing it this way is mainly that You won't have to edit too many config-files, and keep track of all important changes that take place (partition layout & designations, config-files like */etc/fstab* and */boot/grub/menu.lst*... it's tricky business when You're not quite used to it.
And also, the hibernation functionality will be pretty much ready to after this, with very little need for additional configuration.


**Now, here's two in my opinion important considerations for You:**

1. Once You have re-installed Ubuntu, boot up with it and do the extra configuration in */boot/grub/menu.lst* I wrote about earlier (adding this to the end of all "kernel ..." lines (no quotes):
" resume=/dev/sd?" ...
... where the "?" is the swap partition number You'll have, once re-installed.

2. After that, edit the line in Your */etc/fstab* which will look something like this (it must contain "/" before the "ext3"!!):
/dev/sda5    /    ext3    errors=remount-ro    0    1
... and at the first text block to the right after "ext3", insert "relatime,nodiratime," _before_ it, with no quotes, keep the comma, and no additional spaces...
My example line looks like this after such an edit:
/dev/sda5    /    ext3    relatime,nodiratime,errors=remount-ro    0    1

What the above 2nd step does, is tunes how the filesystem is used, for better performance by turning off features that often cause writes after every read on it.
And those features are not needed for most users, not even on the "root" filesystem, it can be useful though on servers etc. where there's a need to keep complete track of access times on files and directories (which is mostly what's written with them on).


I'll try and check back later on this thread to see if You need any more help, otherwise... hope You get this sorted out and can "get down to business"! :)

---

### Post by David_jcd on 2009-09-25
> **FuturePusher said:**
> Sorry to hear something went wrong there...


I'm strongly suspecting You have the "GRUB" boot-sector loader on the NTFS formatted partiton "sda3", right? (You have the "boot" flag set on that partition, so that's where the computer tries to load an OS from at startup..)

Regarding higher speed at different locations of the disk: if I remember correctly, the best throughput is farthest to the "left", and the slowest farthest to the "right" (in graphical representations of a disk)... so Your NTFS partitions are the "fastest".

Unfortunately, one can't move around partitions as conveniently as one would like... it either takes some serious planning in advance, or just accepting a slightly less than optimal setup.


**I think the absolutely easiest & quickest way You can do this, now with You already prepared to reinstall Ubuntu, is to:**

* Use a bootable Ubuntu Live-CD/DVD (do a full "Try Ubuntu..." boot with it) to access Your old "/" partition from there... Purpose: to backup any personal documents/data You may already have stored.

* Delete the old Linux partitions with "gparted" (press "Alt+F2" and type in "gksudo gparted" to run the Gnome Partition Editor, when You're "in" the Live-CD...)
 (You should keep the "Extended" as it's a "holder" for partitions, and already conveniently sized... so just delete "sda5" & "sda6"!)

* Re-install Ubuntu in pretty much the exact same way You did previously, except this time: let the "/" ("root") partition take up 10GB, leaving the rest for the swap partition.
 (I suggest You still use the ext3 filesystem, it's solid, safe & fast once tuned a bit...)

The benefit of doing it this way is mainly that You won't have to edit too many config-files, and keep track of all important changes that take place (partition layout & designations, config-files like */etc/fstab* and */boot/grub/menu.lst*... it's tricky business when You're not quite used to it.
And also, the hibernation functionality will be pretty much ready to after this, with very little need for additional configuration.


**Now, here's two in my opinion important considerations for You:**

1. Once You have re-installed Ubuntu, boot up with it and do the extra configuration in */boot/grub/menu.lst* I wrote about earlier (adding this to the end of all "kernel ..." lines (no quotes):
" resume=/dev/sd?" ...
... where the "?" is the swap partition number You'll have, once re-installed.

2. After that, edit the line in Your */etc/fstab* which will look something like this (it must contain "/" before the "ext3"!!):
/dev/sda5    /    ext3    errors=remount-ro    0    1
... and at the first text block to the right after "ext3", insert "relatime,nodiratime," _before_ it, with no quotes, keep the comma, and no additional spaces...
My example line looks like this after such an edit:
/dev/sda5    /    ext3    relatime,nodiratime,errors=remount-ro    0    1

What the above 2nd step does, is tunes how the filesystem is used, for better performance by turning off features that often cause writes after every read on it.
And those features are not needed for most users, not even on the "root" filesystem, it can be useful though on servers etc. where there's a need to keep complete track of access times on files and directories (which is mostly what's written with them on).


I'll try and check back later on this thread to see if You need any more help, otherwise... hope You get this sorted out and can "get down to business"! :)

Thank you, Pusher, but I already reinstalled ubuntu this morning.
Aniway, i'll surely read your guide again the next time I'll install linux.

I deleted linux partition and moved the data ntfs partition to the right in gparted, so that I had 13 gb at the left of the biggest partition. There I installed Ubuntu (i let the installer do it automatically, cause I had to be pretty shure it would have worked). Result: now it takes the half of the time it took before to boot! 

Thank you again for having spent so much time in helping me!

---

### Post by FuturePusher on 2009-09-26
> **David_jcd said:**
> Thank you, Pusher, but I already reinstalled ubuntu this morning.
Aniway, i'll surely read your guide again the next time I'll install linux.

I deleted linux partition and moved the data ntfs partition to the right in gparted, so that I had 13 gb at the left of the biggest partition. There I installed Ubuntu (i let the installer do it automatically, cause I had to be pretty shure it would have worked). Result: now it takes the half of the time it took before to boot! 

Thank you again for having spent so much time in helping me!


Excellent! :)

No problem, I'm glad to see another person draw benefits from using Ubuntu... I think it rocks the more I get into it!  :guitar:

Also nice to see You getting such a speed increase by not having it at the end of the disk... don't forget to tune the ext3 root filesystem in *fstab* if You want to as well!
(It's not that necessary for You though since You already have all Your larger data on the NTFS filesystems, which don't behave like linux extX filesystems with the "atime" features enabled.)

Rock on! :guitar:

---

### Post by David_jcd on 2009-09-26
> **FuturePusher said:**
> 
Also nice to see You getting such a speed increase by not having it at the end of the disk... don't forget to tune the ext3 root filesystem in *fstab* if You want to as well!
so, if my fstab is
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1a04eb94-c502-4d6d-8438-89673744ce4c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a3a7bf09-4cd1-4825-be29-f7a23e9235de none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2       /media/disco1    ntfs-3g silent,umask=0,locale=it_IT.utf8 0 0
/dev/sda3       /media/disco2    ntfs-3g silent,umask=0,locale=it_IT.utf8 0 0
```

, after editing it should look like this

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1a04eb94-c502-4d6d-8438-89673744ce4c /               ext3    relatime,[COLOR="DarkGreen"]nodiratime,[/COLOR]errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a3a7bf09-4cd1-4825-be29-f7a23e9235de none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2       /media/disco1    ntfs-3g silent,umask=0,locale=it_IT.utf8 0 0
/dev/sda3       /media/disco2    ntfs-3g silent,umask=0,locale=it_IT.utf8 0 0
```

right?

I'd like to monitor the eventual performance improvements using a benchmark, can you suggest me one?
Thanks!

---

