---
title: "swap partition doesn't exist?"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by bosworthy on 2009-01-24
Hi,

I recently installed ubuntu 8.04 on a usb stick, and I am pretty sure I did not setup / define a partition when I went to do a manual install from the livecd.  I'm a newbie.

Now, when I Suspend, it won't wake back up.. my mouse lights up, but the usb stick does not light up.  I tried to hibernate, then I get this error message:

[177.036387] i8042 aux 00:07 activation failed
[177.584950] swsusp: cannot find swap device, try swapon -a

Do I really need a swap thingy?  I was thinking of using tmpfs (so I've read) so that I can prolong my usb stick.  Even with tmpfs, do I still need to define a swap thingy?

Anyone have a laptop and has successfully used tmpfs?  I tried to google, but I'm not sure what the tmpfs command options do..I've also read about compatibility issues.  what about ramfs?

Appreciate any help.
Thanks.

---

### Post by Mark Phelps on 2009-01-24
Yes -- you do really need a "swap thingy" in order to do hibernate.  That's where it writes the image it uses to restore the desktop after you restart.

Run the partition manager to confirm you don't have a swap partition.  If you let the installer create the partitions, you should have a swap partition.

---

### Post by bosworthy on 2009-01-24
I'm a newbe.  I'm sorry, how do I run the partition manager?  I don't plan on reinstalling the OS again.. i just want to add a swap partition... and how big should this be?

I'm reading up on:
[http://ubuntuforums.org/showthread.php?t=1042946&highlight=add+swap+partition](http://ubuntuforums.org/showthread.php?t=1042946&highlight=add+swap+partition)

Thanks.

---

### Post by bosworthy on 2009-01-25
to other newbies:  I think i'm going to start posting only at the beginner's only forum:

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

[http://ubuntuforums.org/showthread.php?t=1032307&highlight=swap](http://ubuntuforums.org/showthread.php?t=1032307&highlight=swap)

:)

---

### Post by bosworthy on 2009-01-25
I'm a newbie, and I just realized that the following is a source for knowledge :)  sure beats the heck out of asking and searching the forum!

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

in general:

ubuntu.com  then go to documentation. or:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

then select the right version then have yourself a blast!  it's alphabet order and it's a holy gopher hole ! 8)

---

### Post by bosworthy on 2009-01-25
I think this is the most helpful of all pages: 

[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

:)

---

