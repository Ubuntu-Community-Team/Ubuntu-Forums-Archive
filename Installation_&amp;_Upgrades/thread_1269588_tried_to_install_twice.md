---
title: "tried to install twice"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by keithpup on 2009-09-18
I installed ubuntu Jaunty Jackalope twice on a dell inspriron desktop (two hdds & 1 gb ram DDR2 + two year old Video Card Nvidia) and it runs XP fine, but both times I get Grub 21 errors. 

I need some help figuring out how to clea out the two failed installs and if I need to check something to see why I get these grub errors.

Help?
:popcorn:

---

### Post by daevski on 2009-09-18
If you put in the live disc, you can select "Install Ubuntu" from the main list and then when you get to the partioning hard drive select section, you should select manual partitioning.

You will see the XP partition in FAT or NTFS file system, and linux in SWAP, EXT3, EXT4 or similar formats.

just delete the linux ones and make a New partition for your next install. Make 2 actaully, One Logical Swap space of about 512mb and another New one of Primary ext3 and make it however big you want to have sectioned off for Ubuntu

---

### Post by oldfred on 2009-09-18
Some explanation of Grub 21 errors which may help you understand why you are getting that error:
from Herman's site
[http://members.iinet.net.au/~herman546/p15.html#21](http://members.iinet.net.au/~herman546/p15.html#21)

---

### Post by keithpup on 2009-09-18
w00t! things to try when I get home.
I guess I am spoiled, I installed BSD for a while to use DD and some other utilities but before that the only Linux exposure was to Knoppix, the first time I installed Ubuntu was to a test box here at work to see if Civil 3D would run (it did) and it was simple and flawless.
Did it at home with my son as a fun (and I thought easy) project now that I did a repair on XP (nothing would boot once I got the grub error) I am ready to try for a third time.
Thanks guys!:guitar:

---

