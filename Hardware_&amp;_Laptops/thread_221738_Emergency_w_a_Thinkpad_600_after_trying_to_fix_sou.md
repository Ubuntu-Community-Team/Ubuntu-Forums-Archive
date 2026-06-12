---
title: "Emergency w/ a Thinkpad 600 after trying to fix sound"
date: 2006-07-23
forum: Hardware &amp; Laptops
---

### Post by shapiror on 2006-07-23
Hey, I'm having a bit of a problem.  I tried to do the fix that is posted here [http://ubuntuforums.org/showthread.php?t=188736]("http://ubuntuforums.org/showthread.php?t=188736") for the sound card, now I cant even boot up the laptop.  It gets past the boot loader and gets to the point where it says:

Loading essential drivers...           OK
Mounting root file system...

And that's it.  It just stops there.  Did I do something wrong with that sound card fix?  Is this a common problem?  How do I fix this?

-Randy

---

### Post by anothertallorder on 2006-08-31
Thank goodness I am not the only one to have had this problem with this, I have followed the same tread and come had the same same result.
the way I delt with it was to boot at the first grub boot text hit "escape" This give you the option the "save boot" to a terminal "root" use's. Here I found the "menu.ls" file that I edited in /boot/grub/ and used "vi" editor
It was a command like:
vi menu.ls 
this opens the file and you can remove the appendments you made (just back track on what you did in the tread) Now please check out vi commands before doing this. I found 'saving' quite hard, Im sure someone could come in here and explain this better. :qw was something to do with it.
If you can save the menu and do the 'update-grub' command. reboot and you should get in...
I have tryed this tread again with the same results, this time I made a backup copy of the menu file.

My sound dosn't work, but I can boot..hope I was some help...

---

