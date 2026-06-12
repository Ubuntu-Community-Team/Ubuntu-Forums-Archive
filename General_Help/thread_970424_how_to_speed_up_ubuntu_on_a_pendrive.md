---
title: "how to speed up ubuntu on a pendrive?"
date: 2008-11-04
forum: General Help
---

### Post by bsh on 2008-11-04
hello all
i have a "swiss knife" usb thumb drive with ubuntu installed on it.
problem is, it's writes data quite slow, and most significantly, it suffers from very low numbers of i/o operations per second.

i tried to make it as fast as possible, by using xfce (that's my favourite anyway!), disabled the system logging, put temp and other filesystems onto virtual "ramdisks", and of course there's no swap at all.
it now boots pretty quick but is still unusable, most of the times the system "hangs", waiting for i/o operations to complete, etc.

so my question is, what other steps can i do to redoce writes to the absolute minimum?
thanks in advance.

edit: i've been googling for this a lot, but only found how-to's on how to install ubuntu on a pendrive, but nothing about how to make such an installation quicker.

---

### Post by C.S.Cameron on 2008-11-04
Formatting "/" and "/home" partitions using reiserfs seems to make a thumb drive run faster and smoother to me.

---

### Post by snowpine on 2008-11-04
Hi there, first of all, Cameron is an expert on USB installs, so definitely good advice there...

My suggestion is this. There are 2 types of pen drive install, a full install (which is what you appear to have set up) and a Live USB install. A live USB install is just like a live CD, which means it is read-only and there are zero writes to your device. This should be quite a bit faster. The downside of course is that it's read-only, however, the best of both worlds is a persistent live USB where the root filesystem is read-only, but your /home directory is read/write.

ps USB devices are always going to be slower than internal hard drives; it is the "nature of the beast."
ps There are also very small distros such as SliTaz or Puppy that are ideal for a USB device.

---

### Post by LowSky on 2008-11-04
usb 1.1 is alot slower than usb 2.0

make sure you using the correct port, some computers have both, and much older computer only have the older

---

### Post by philinux on 2008-11-04
You could try System>admin>create usb startup disk. It might be quicker.

---

### Post by bsh on 2008-11-05
> **C.S.Cameron said:**
> Formatting "/" and "/home" partitions using reiserfs seems to make a thumb drive run faster and smoother to me.

isnt' reiser a journaling fs? i assume in that case i would have to turn off journaling.
i use ext2 because it's not journaling and thus reduces disk i/o further.
but i'll experimetn with reiser if i'll have some time. thanks for the tip.

---

### Post by bsh on 2008-11-05
> **snowpine said:**
> Hi there, first of all, Cameron is an expert on USB installs, so definitely good advice there...

My suggestion is this. There are 2 types of pen drive install, a full install (which is what you appear to have set up) and a Live USB install. A live USB install is just like a live CD, which means it is read-only and there are zero writes to your device. This should be quite a bit faster. The downside of course is that it's read-only, however, the best of both worlds is a persistent live USB where the root filesystem is read-only, but your /home directory is read/write.

ps USB devices are always going to be slower than internal hard drives; it is the "nature of the beast."
ps There are also very small distros such as SliTaz or Puppy that are ideal for a USB device.

thanks i know all of that.
i can still boot my existing install in read only mode if i wish. and only boot rw, if i want to update/install anything.

---

### Post by C.S.Cameron on 2008-11-05
My reiserfs disk does not seem to flash more than my persistent one, even with swap space.

Intrepid's USB installer does not come with, nor work with Xubuntu, nor with 8.04.1.

You can make a usb-creator install part time persistent by checking "Discard on shutdown" and making two ext3 partitions, one labeled casper-rw and one home-rw. F6, (space)persistent at boot will make the session persistent.
This method also works with a Unetbootin install of Xubuntu.

A Reiserfs disk sometimes takes a while to boot, if it decides to check the filesystem, however I suggest it worth checking out.
My Reiserfs disk has been working well for a few months now.

---

### Post by bsh on 2008-11-05
i have not much of an ide why are you talking about intrepid and persistent install and xubuntu and unetbootin and stuff?
as said, i already have 8.04.1 it installed on the drive (installed from another pendrive, lol) and i'm not planning to do it again.
i want to speed up the existing one, not to do a fresh install or so.
that reminds me i have to check out one thing that i forgot to configure, maybe that will help... :)

---

