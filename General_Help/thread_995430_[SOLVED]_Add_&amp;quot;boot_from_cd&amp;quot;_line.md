---
title: "[SOLVED] Add &amp;quot;boot from cd&amp;quot; line to GRUB"
date: 2008-11-27
forum: General Help
---

### Post by Trzone on 2008-11-27
I would like to know if it is possible, and how to add a "boot from cd" line to GRUB? 

It would be pretty nice to have :)
I know how to use a terminal! :P
thanks!

---

### Post by RealPSL on 2008-11-27
I have not tried this and editing the menu.lst time is always a challenge. The live cd has this boot from cd menu item item so if you boot from the live cd and run cat /boot/grub/menu.lst you should be able to just extract the lines from there and add it to your "real" /boot/grub/menu.lst.

---

### Post by logos34 on 2008-11-27
here's [one]("http://ubuntuforums.org/showthread.php?t=374555").

There's another howto in the outdated tips & tutorial section I used to set up mine, but can't for the life of me find it now

---

### Post by Trzone on 2008-11-27
You follow the links instructions
but you must specify the root partition

title		Boot from CD
root		(hd0,4)
kernel 		/memdisk
initrd		/sbm.bin

Mine is (hd0,4)
It's the same one as your other linux images
However, this seems to be an entire boot manager, works the same :) heh
This could be very useful on older computers
thanks!

---

