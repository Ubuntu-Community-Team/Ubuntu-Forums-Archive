---
title: "can't find my cdrom"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by AllenDowney on 2007-06-12
I just finished my first ubuntu install, which went well except for two things
that might be related:

1) When booting, the system hangs for a couple of minutes with just a few
pixels on the progress bar.  Any way to get the details to see what the hangup
is?

2) Ubuntu doesn't know I have a cdrom, even though I installed off it.

The cdrom is pretty generic and not all that new, so I'm a little surprised.
If it would help I could get some info off it, but before I rip open the box I wanted
to make sure I'm not missing something obvious.

Thanks for any help.
Allen

---

### Post by swudee on 2007-06-13
Hi Allen

Looks like no one has any answers for you.
As for the slow boot. Are you leaving any discs in the CD drive during boot. If so LVM takes some time with those during boot, really bad with DVD's!
CD drive. There will be no icon on the desktop for the CD drive if there are no discs of recognized format in it. You can see if it is mounted by going to "Places" on the top tool bar,
then computer, file system, media. It should be listed there.

Hope that is of some help

David

---

### Post by carlos.gil on 2007-06-13
I have exactly the same problem in kubuntu.

Any ideas to solve it?

---

### Post by AllenDowney on 2007-06-13
I made some progress on this problem since my last post.  It looks like there is a conflict
of some kind between my cdrom and my slave drive.

1) If I unplug the slave drive, I get a fast boot and I can access the cdrom.

2) If I plug the slave back in, the boot gets hung at the point where it is "waiting for root file
system" or something like that.

        (the way I got that information was be editing /boot/grub/menu.lst and removing the quiet option)

The resolution of the conflict seems to be non-deterministic; that is, sometimes the cdrom is
visible, sometimes the slave drive is visible, and I think I had both once, but I'm not sure.

Anyone have any hints?

Cheers,
Allen

---

### Post by kazuya on 2007-06-13
Is this Feisty 7.04, or Linux Mint 3.0.

Also, after install do an update of system. Kernel update may help. Ensure that drives are well connected. What are the system Specs?

I had similar issue with previous Feisty beta CDs, not the final one though.

---

### Post by AllenDowney on 2007-06-13
Thanks for the followup.  This is a fully updated Feisty.

Tonight I will use dmesg to get a better idea of what is happening during
boot and post more info.

Cheers,
Allen

---

### Post by neorou on 2007-06-13
Allen,
Just a thought, but to make sure all of your hardware related issues are set aside, you may want to reset your CMOS chip. Especially if you are sure that all the connections are in place.

A lot of my install problems had to do with the motherboard frazzling out.

Good luck.

---

### Post by neorou on 2007-06-13
By the way, I forgot to provide a generic link regarding what I just said. Here's one I pulled of a web search:

[http://www.jrpcrepair.com/cmosreset.html](http://www.jrpcrepair.com/cmosreset.html)

---

### Post by carlos.gil on 2007-06-13
Great news! I solved it. 

I followed this

[http://ubuntuforums.org/showpost.php?p=2501270&postcount=64](http://ubuntuforums.org/showpost.php?p=2501270&postcount=64)

---

### Post by AllenDowney on 2007-06-13
I have more information.

First, the issue is not the slave drive.  That's working fine.

The key variable is whether or not there is a cd in the cdrom drive.

_Without_ a cd, I get a slow boot (hangs at "Waiting for root file system."),
and I can't access the cdrom.  It appears in Places->Computer, but if I
click on it I get an error window with "/dev/scd0 does not exist"

If I put in a cd after boot, it spins for a while but doesn't appear on the desktop.

If I boot _with_ a CD, I get a faster boot and the cdrom works.  The entry
in /etc/fstab is

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

So there we are.  My only theory at this point is that it is trying to boot
from cdrom, taking a long time to time out, and then... ok, that's all I've
got.  Anyone?

Cheers,
Allen

---

