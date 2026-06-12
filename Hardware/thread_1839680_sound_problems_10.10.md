---
title: "sound problems 10.10"
date: 2011-09-06
forum: Hardware
---

### Post by treepete on 2011-09-06
hi. i'd really appreciate some help with this...

my original problem was that headphones were not recognised and wouldn't turn off internal speakers.

i have been trying a number of different fixes found on other threads... but i seem to be digging myself into a deeper hole.

my problem now is that i have no sound: 
-terminal says it cannot open mixer because no such file is found.
-sound options only give me dummy output.
-i've lost the sound applet.

so, i'd like to fix those issues + the original one.

i am running 10.10 on a lenovoG470.

thanks a lot :)

---

### Post by .... on 2011-09-06
Those issues all stem from the same cause: you borked the kernel module. Try reinstalling the appropriate linux-image package for your kernel. If that doesn't work, try this script before you give up and reinstall: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by treepete on 2011-09-14
thank you...
that first fix worked.
and the original problem (headphone not recognised) has been fixed too:

[http://ubuntuforums.org/showthread.php?p=11250641#post11250641](http://ubuntuforums.org/showthread.php?p=11250641#post11250641)

v

---

