---
title: "Ubuntu 8.10 won't start on my Dell Dimension 2400"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by pachao on 2009-02-02
I have decided to switch my Dell to use Ubuntu 8.10. The OS was successfully installed onto my harddrive. During the start up, I can get to the log in page, but then after the log in Ubuntu hangs with its orange background...forever. I've tried with the recovery mode, but nothing changes. And also, during the hanging, my key board stops functioning (i.e. when I try to hit caps lock key, no light would turn on), so I can't check system processes using ctrl-alt-f1?. Hope you guys can help me figure this out. I would highly appreciate any suggestions.

---

### Post by danwebb on 2009-02-03
During my install on my desktop it did not hang up the CD player kept beeping the whole time. Did you chose the option to Check the disk for errors, before the install?

---

### Post by tommcd on 2009-02-03
At this point it would be a good idea to bootup the Ubuntu CD and check the disc for errors as Danwebb suggested just to rule out a corrupted iso as the problem.

If the disc checks out ok, then boot to recovery mode and choose the option **xfix Try to fix the xserver**. It is possible that your video card or monitor are not properly configured.

And welcome to the Ubuntu forums!

---

### Post by pachao on 2009-02-03
I've tried to do a disk check from the cd, it tells me there are no errors. I also tried to do the server xfix from recovery mode, and again it tells me everything is fine. The problem remains. But thanks for your suggestions anyways. Any other way that I can get it to work?

---

### Post by tommcd on 2009-02-04
How much memory is in that computer? If it is less than 512mb, upgrading the memory may help according to this thread:
[http://ubuntuforums.org/showthread.php?t=386920](http://ubuntuforums.org/showthread.php?t=386920)
Also see post #21 of that thread. Your problem *may* be related to the boot splash screen. You can disable the splash screen temporarily to test it like this:
As the computer boots up you will see the grub menu. If you don't see the grub menu on bootup, hit the **Esc** key to see the grub menu. When you are at the grub menu, hit the "e" key over the entry for Ubuntu to edit that entry. Then use the arrow keys to come down to the kernel line. Hit the "e" key again to edit the kernel line. At the end of the kernel line will be the words **quiet** and **splash**. Use the backspace key to reomove those 2 words *only*. Then hit enter, then hit "b" to boot. You will see a lot of text scroll by before you get to the login screen where you enter your user name and password. This will not make any permanent changes to the grub menu. If the computer now boots ok, then remove the words quiet and splash permanently from grub's menu.lst as explained in post #21 of that thread.
EDIT: I just realized after rereading your first post that your problem happens after the login screen. But try removing the quiet splash anyway. It can't hurt. 

Also see post #22 in the same thread. That user got Ubuntu to work by entering the computer's BIOS and reducing the video memory to 64mb.

If you do get Ubuntu to boot ok, consider increasing the memory if you have less than 512mb. 1GB of memory would give the most bang for the buck.

---

### Post by MyR on 2009-02-27
the problem is from compiz

see thread [http://ubuntuforums.org/showthread.php?t=970037](http://ubuntuforums.org/showthread.php?t=970037)

peace

---

