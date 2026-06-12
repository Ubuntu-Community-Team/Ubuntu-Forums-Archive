---
title: "how to create /boot mount but with a /boot directory"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2009-10-07
Upon booting up I get: "Grub Error 15."

(same error I get if I boot up Live HardyHeron CD and run:
  sudo grub
  find /boot/grub/stage1
)

I believe I know why I am getting the error, but I don't
know how to solve it.

I am trying to install HardyHeron with hard disk encryption
on a machine that has Windows on it, with SafeBoot hard
disk encryption.

I've followed the instructions on the forum;
One creates a regular /boot partition, then an encrypted logical
volume partition, etc.
All that is good so far.(i think)

So here is the rub.
The /boot partition has no "/boot" directory.

Hence why the grub command of `find /boot/grub/stage1` fails
with "Error 15".

Although, the command of `find /grub/stage1` returns, (hdo,2),
which is correct.

Now during the Hardy encryption install, I told it to write 
the grub loader to my partition #3 (the /boot partition) 
and not to hd0, since
SafeBoot owns the MBR and cannot be overwritten.
(cause that's another rat's nest)

This Safeboot MBR, I surmise, loads up the old MBR that was
created by a previous installation of Linux (from some
secret location), and this old MBR must
have the specification, of "go find /boot/grub/stageX".

So since I cannot re-edit or clobber this old MBR, 
to tell it to instead "go find /grub/stageX"
nor can I clobber the actual MBR (a SafeBoot-ized MBR)
is there a way to create a "/boot" partition, that actually
creates a "/boot" directory?

Or is there something that I can do to my current /boot partition
to get the job done.

For example, is there a way with this Live CD to mount
this /boot partition, then once there run these commands:
 cd /
 mkdir boot
 mv grub  boot
 mv <other files at the root> boot

Or something that gets me the same effect.

Anyone follow it this far?

---

### Post by gmoore777 on 2009-10-07
ok, so this just solved my first problem:

Boot up Live CD.

In a terminal window:
 sudo /
 sudo mkdir pig
 sudo mount -t ext3 /dev/sda3 /pig
 sudo cd /pig
 sudo mkdir boot
 sudo mv grub boot
 sudo mv *all the other files* boot

Reboot.

Instead of getting Grub Error 15,
i am at a grub prompt. So that's better, but not what I 
was hoping for.

I'll Google to see how to boot up that encrypted partition
from this point.

---

### Post by gmoore777 on 2009-10-08
Answering my own question:

To continue from the Grub prompt(for my specific case):

configfile (hd0,2)/boot/grub/menu.lst

And to prevent this problem from happening in the first place:

grub > root (hd0,2)
grub > setup (hd0,2)

(and that's because the stage2 binary has the path to the
configuration file hardcoded in it.
$ sudo strings stage2 | grep menu
/grub/menu.lst
/menu.lst


After the re-installing GRUB to partition#3, I get:
$ sudo strings stage2 | grep menu
/boot/grub/menu.lst
/menu.lst
)

This case is closed.

---

