---
title: "[SOLVED] Fixing boot up - 8.04"
date: 2008-08-11
forum: General Help
---

### Post by lawentzel on 2008-08-11
I have a laptop.  It ran version 8.04 flawlessly.  Had no problems. Suddenly it stopped booting up.  The hard drive is brand new as of 8 months ago, so not likely a bad hard drive.  Is there a way to fix a Linux installation?  Installing Linux over top of an old installation?  Is there a way to force it to check the hard drive and fix any potential errors?  Any help would be appreciated.  Thank you very much.  I just am trying to avoid formating and reloading the computer.  Too much on it that I haven't back up.  (Yeah, shame on me, I know.)

Lee

---

### Post by Krupski on 2008-08-11
> **lawentzel said:**
> I have a laptop.  It ran version 8.04 flawlessly.  Had no problems. Suddenly it stopped booting up.  The hard drive is brand new as of 8 months ago, so not likely a bad hard drive.  Is there a way to fix a Linux installation?  Installing Linux over top of an old installation?  Is there a way to force it to check the hard drive and fix any potential errors?  Any help would be appreciated.  Thank you very much.  I just am trying to avoid formating and reloading the computer.  Too much on it that I haven't back up.  (Yeah, shame on me, I know.)

Lee

Try booting with a live CD and check your '/boot/grub' directory... make sure 'menu.lst' is there and that it has the right info in it.

Also, make sure the symlinks to the kernel stuff (initrd.img and vmlinuz) are in the root of your Ubuntu drive and make sure they point to the right files (which should be located inside '/boot').

Did you add, remove or change any drive configurations in your laptop (or plug in a removable USB drive)?

The line that says something like 'root (hd0,0)' may no longer be valid if you changed drive configurations. 

That's all I can think of for now. Good luck!

-- Roger

---

### Post by lawentzel on 2008-08-11
Booting up in recovery mode, the last line I see is:
```
[  10.471876] Checking 'hlt' instructions... OK.
```

---

### Post by lawentzel on 2008-08-14
Booting off of a live CD allowed me to back up everything before formatting and reloading.  So... Happy enough.

---

