---
title: "[SOLVED] Unable to boot to windows after re-installing grub"
date: 2008-11-15
forum: General Help
---

### Post by TheSerious on 2008-11-15
After I followed this tutorial: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I'm getting an error when trying to boot into windows (after configuring it with grub as listed in the first entry):
"Error 13: Invalid or unsupported executable format"
This is after I've configured grub and changed the menu.lst under /boot/grub/ to reflect exactly what the guide said. my hd is (hd0,0)..

First time with linux but I'm better than the average user with computers. Anyhow, my windows partition is still in-tact, I can see it when booting into ubuntu. I'm on Intrepid (8.10) if that makes a difference?

Anyhow, help on this would be much appreciated =)

---

### Post by TheSerious on 2008-11-15
haha fixed it! *Whew* I was afraid I wasn't gonna get my fill of wrath today haha. So this is what I learned: (hd0,0) refers to first harddrive (hd0) and the 2nd zero refers to the 1st partition on the drive. My windows was on the second partition so I just had to change it to (hd0,1). Hopefully this helps anyone.

thanks to stalebrew!
([http://www.webdeveloper.com/forum/showthread.php?t=174383](http://www.webdeveloper.com/forum/showthread.php?t=174383))

---

### Post by Mr_JMM on 2008-11-15
If your problem is solved can you please mark the thread as Solved?

"Thread Tools" - > "Mark as Solved"

---

