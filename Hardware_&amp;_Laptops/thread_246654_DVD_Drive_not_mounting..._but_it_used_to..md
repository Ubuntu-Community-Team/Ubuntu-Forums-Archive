---
title: "DVD Drive not mounting... but it used to."
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by sleepingdragon on 2006-08-29
The same problem is back, but it has turned into a handy little solution. My niece has discovered the joys of installing software. Now, with the DVD locking out, I can restrict what she can/cannot install. I've created a couple of handy icons with the mount and umount commands - all I need is my password to lock/unlock my drives. Perfect.

==========================================================================


OK, that wasn't much fun, I decided to reinstall from scratch, it was a lot easier. At least having a dual-boot means that you have at least one OS to work with. So, I'm up and running again  and hopefully it'll be more stable this time.

=========================================================================

On top of all this now, my system just went down. I'm getting the XServer message as shown on the update message on the front of this site, but i've already got the latest update which should correct that problem. I can still login, but after a short amount of time everything hangs. There's a lot of screen messages, scrolls too quick to read, something about a kernel crash and PPP (?) 

I REALLY, REALLY hope someone can help with that one, I don't need this as an intro to an otherwise excellent OS. 

==========================================================================

Heya, I'm new to Linux (running on DD6.06) and I think I'm doing pretty well, nothing has caught fire... yet. However, I've now got a problem with my DVD-RW drive, the damn thing won't mount on boot. I'm not getting any error message, but if I try to run a DVD movie, I'm told I need superuser permission to mount the drive. I can mount it manually by "sudo mount /dev/dvdrw", and giving my password, the DVD icon appears on my desktop but Kaffeine won't run it unless i manually navigate it to the VIDEO-TS folder on the disc and select the first .VOB file i come across. DVD playback seems fine once it's running. One other thing, when I checked the permissions for the drive, the owner was listed as "unknown". I can chown this to root, but it seems to go back to an "unknown" owner.

In my /etc/fstab file, I've noticed that only one DVD drive is listed (I do have two - one DVD-ROM and one DVD-RW, the DVD-ROM works fine with normal auto playback behaviour). This singular drive is listed as 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
_/dev/hdd        /media/cdrom0   udf,iso9660	user,noauto     0       0_
none            /selinux        selinuxfs       noauto  0 0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

Shouldn't there be two cdrom drives listed? Hope somebody can help on this, it's more of an annoyance than a serious operating problem, but at least i'm getting some pratice in running command-lines! :D

---

### Post by rbmorse on 2006-08-29
Of no help but perhaps some consolation, I have the same problem. My optical drives are both Plextor DVD writers, one an IDE model and the other a shiny new SATA interface model.  Dapper is decidedly unhappy with this arrangement although either drive works fine if installed as the only optical drive. 

Like you I can use both drives by manually mounting them, or simply giving the application a discrete path to the device (either /dev/hdc or /dev/scd0 depending). 

Fooling with fstab doesn't seem to make much difference, but it is entirely possible I have yet to invoke the right majick spell there. 

I've also found the player VLC is a little more forgiving of whatever the problem happens to be with the way the drives are (or are not) recognized and mounted. 

In any case, I'm still trying to figure out what is going on.

---

