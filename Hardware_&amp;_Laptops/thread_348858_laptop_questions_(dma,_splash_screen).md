---
title: "laptop questions (dma, splash screen)"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by mikeymikec on 2007-01-29
On Edgy, the OS loading progress screen won't show on my Dell C400 laptop.  Is there some way I can tweak the settings it tries to run on, or at worst knock it down to text-only?

Secondly, how do I know if my storage devices are running in DMA mode?

---

### Post by allwin on 2007-01-29
You can get it to boot in text mode.  When you get to the boot screen, type "e" to edit the first line.  Type "e" again and remove the words quiet and splash.   Then type a "b" to boot.  Now you should see lots of text.  Some laptops have a BIOS mode that displays 640x480 in the center of the screen instead of stretching it all over.  Check if you have that, maybe there's something you can do there.

Try going to a terminal and typing "sudo hdparm -iI /dev/hda" and see what it reports about the hard drive settings (hoping your HD is actually /dev/hda).  You can then "sudo hdparm -d1 /dev/hda" if it's not on.  Permanent cure involves changing your fstab (google for directions there).

Also, you can remove the "quiet" option permanently...google for "menu.lst" and how to change that file.  There are some gotchas there because if you change the wrong lines, a software update in the future might overwrite your customizations.  This is a trick file where their are ACTIVE lines that look like they are commented out.  Don'cha love it!

---

