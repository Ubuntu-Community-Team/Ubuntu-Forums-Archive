---
title: "volume buttons not working but still works when changed manually"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by dhabell@yahoo.com on 2007-11-13
the volume buttons(near the play and fast forward buttons) are not working on my acer laptop.  I am running gutsy.  they used to work when I first installed ubuntu.  I can still change the volume manually up in the corner of the screen though.

---

### Post by qbox on 2007-11-13
Do you mean on extra buttons?
Ok try this.

=====================================================
Update Grub
upon initial boot, I hit esc to enter grub. Then I pressed e to edit top entry then e again on the line with all the options. At the end of the line I removed the quiet splash and added pci=assign-busses

I want to have all the text fly by upon start up, so I kill the quiet and splash.

To make the Grub edit "stick", you will need to do these steps:
If you edit your menu.lst manually, you want to make sure to edit the "# kopt=" line (leave it commented), or the "# defoptions" line, then run "sudo update-grub".
If you manually edit the options on the boot line of your various kernels, they'll be wiped out each time menu.lst gets updated (by having a new kernel installed, for example).

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=792 pci=assign-busses

I added the RED text to the file and then ran sudo update-grub and reloaded the menu.list file and the change now shows up on all entries!
(you will be able to log into a GUI environment here!)
====================================================

Thanks to cacycleworks this help me to figured out how to make some thinks to start work. I paste upper text from [http://ubuntuforums.org/showthread.php?t=518702](http://ubuntuforums.org/showthread.php?t=518702)

---

