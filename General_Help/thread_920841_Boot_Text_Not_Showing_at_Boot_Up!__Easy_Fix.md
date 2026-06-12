---
title: "Boot Text Not Showing at Boot Up!  Easy Fix?"
date: 2008-09-15
forum: General Help
---

### Post by Kellemora on 2008-09-15
Boot Text Not Showing During Boot-up?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

I don't know about the rest of you, but I HATE looking at a blank screen and NOT knowing what's going on during boot-up.

If you would like to see just what's going on during boot-up, here is a quick and easy way to make it happen!

Left Click on Applications, from Accessories select Terminal.

In Terminal type  gksu gedit /boot/grub/menu.lst (if you are using grub that is).

If you are multi-booting several Distro's select the first Ubuntu entry, which is the normal boot.  There will also be a Recovery boot, normally under it, and possibly a memtest under that.

In the Normal Boot listing you will see a line that reads 'kernel' /boot/vmlinuz at the end of this line, after the 'ro' you will find  the words 'quiet' and 'splash'.

See OPTION below line that reads SAVE and Exit.

Simply remove these two words, leaving everything else intact.
Don't worry about the word 'quiet' under initrd in the left column.

SAVE and Exit.

OPTION:  As a precaution, you may want to Comment out the existing line by placing a pound sign and a space (# ) in front of the existing line, then copy and paste it below the original.  Uncomment the new line by removing the pound sign and make the changes to this new pasted line.  You can always comment out the new line and uncomment the original line and be right back where you were before making any changes.

When you reboot, you should see all the boot-up text just as in other Distro's!

To Undo, just follow the above directions to put back the two words you removed.

The above was tested on the following machines with complete success:
HP Pavilion 753n, 2.53GHz Intel P4, 512mb, Intel 82845G/GL video card.
e-machines T4165, 1.6GHz Intel P4, 256mb, AGP 3D video card.
Compaq 5420, 1.47GHz Athlon XP1700, Savage 4 AGP video card.
e-machine T6524, 2.30GHz Athlon 64-3500+, ATP Radion Express 300 video card.


TTUL
Gary/aka Kellemora
9/10/08 – rev 9/15/08

---

