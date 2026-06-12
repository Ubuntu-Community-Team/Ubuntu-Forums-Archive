---
title: "GRUB 1.97 beta freezes in 9.10"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Chuckgofer on 2009-11-04
GRUB freezes on me whenever I move down in the GRUB menu.  I dual boot, but I can't even get to the Windows XP option, as GRUB freezes whenever the selector is over Recovery Mode.  Any ideas/suggestions?  I was hoping to see if There would be a software update that might fix it, but I can't wait that long.

---

### Post by dazer26 on 2009-11-04
I had a similar issue on my laptop, only grub froze as soon as the menu appeared.  You can try logging onto you install from a live cd and doing a "sudo update-grub", although this made no difference to me.
Here is a link on how to use the live cd to log onto your install

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

and if that doesn't work as it didn't for me, you can remove grub2 and put the trusty .97 grub back on your computer.  This link will tell you how to do that.

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

---

### Post by Chuckgofer on 2009-11-04
Well, I can still boot into Ubuntu.  So it doesn't freeze at that point. But when I move down the menu, GRUB freezes.

And updating grub is basically useless. :(

So Yeah.  best option so far is installing old grub :(

---

### Post by Chuckgofer on 2009-11-04
Any other suggestions?  I'd really like to get this GRUB problem solved.

---

### Post by nikon858 on 2009-11-18
I'm having the exact same issue, same version of grub and ubuntu...older AMD HP Laptop....have you figured out a fix to this yet? Cause I'd really like the option to boot back into my xp install....and I'd rather not downgrade to the old version of grub...

---

### Post by Mujaheiden on 2010-01-25
Its been a few months, have you managed to solve this issue? I just installed 9.10 on a Sony Laptop. After updating the packages I cant move down in the grub menu - it freezes.

Luckily I prioritized the Windows boot already, but I'd like to get access to Ubuntu too. Something a live disc can solve?

See [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/453369](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/453369) :(

---

### Post by tarwood on 2010-01-27
I also have an older Compaq(HP) with an AMD 2000+ 1GB ram, that is having this exact issue. I am able to press one key and than it locks up. If I let it time out, it will boot into Ubuntu, or if I press enter. If I press anything else, "e" "c" anything, it locks up. This is extremely annoying, as I do plan on transitioning over to Ubuntu, I still want this problem fixed. If I were to dual boot with anything else I would be also stuck. Please assist. Thanks.

---

### Post by Mujaheiden on 2010-01-27
The second link of dazer26, installing legacy grub, worked for me, but admittedly, its a workaround. Bug report is here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/453369](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/453369)

---

### Post by s.aschen on 2010-01-29
A work around I have been using is to pre-load the keyboard buffer.  My Windows entry is 6 lines below the top entry, so when I see the "GRUB Loading..." text I very quickly tap the down arrow 6 times and then hit enter.  You must be fast!

I've also seen this tool freeze on subsequent boots if you try to use the keyboard buffer trick to boot into recovery mode.  Recovery mode is frozen solid and you have to reset the system.  When the system comes up again it just shows the boot menu, no countdown, and goes nowhere.  Use the above trick again and on the next boot the system will countdown and launch the default entry provided you don't touch the keyboard again.

A real pain this thing is!

---

