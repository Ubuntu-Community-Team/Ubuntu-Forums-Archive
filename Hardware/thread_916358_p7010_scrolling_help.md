---
title: "p7010 scrolling help"
date: 2008-09-10
forum: Hardware
---

### Post by the_poolster on 2008-09-10
I have just installed Hardy Heron on my Fujitsu-Siemens P7010. What a joy that everything works! All except, that is, the scroll button on the mouse pad. It's always the trivial little things, but it's driving me nuts.

I have searched all over forums dealing with similar problems and nothing seems to make any difference.

Step 1 was to install the gsynaptics thingumy and change the properties that way. Didn't work. Error message saying SHMConfig must be set to true in xorg.conf.

Step 2 edit xorg.conf to allow acces to gsynaptics. Didn't work, still can't get into gsynaptics. Tried true, True, On, on, even 1. no luck.

Step 3 was trying to add the line i8042.nomux=1 to the grub boot line. Didn't work.

Step 4 was to edit xorg.conf directly to affect changes in mouse behaviour. Nothing changes. Can't even speed it up.

Please, can someone help me with this very annoying, but not very critical problem. TIA. I can post my xorg.conf if you like, but which one!? There is a load that do nothing!

---

