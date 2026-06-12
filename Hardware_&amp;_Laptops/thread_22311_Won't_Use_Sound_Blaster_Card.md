---
title: "Won't Use Sound Blaster Card"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by Recked on 2005-03-26
Hello,

I am going nuts!!!!  I have read many of the posts regarding sound issues and am still not able to get sound to work via the Sound Blaster card installed. Sound will work from the chipset built into the motherboard. The last post I read mentioned making a change to the below, but there isn't any listing whatsoever regarding a sound card so I have no idea what should be in there.

Any help would be appreciated and thanks in advance.

 /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod

---

### Post by trigg on 2005-03-26
[QUOTE=Recked]Hello,

I am going nuts!!!!  I have read many of the posts regarding sound issues and am still not able to get sound to work via the Sound Blaster card installed. Sound will work from the chipset built into the motherboard. The last post I read mentioned making a change to the below, but there isn't any listing whatsoever regarding a sound card so I have no idea what should be in there.

Any help would be appreciated and thanks in advance.

 /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod[/QUOTE]


Which sound card do you have? (exactly)

and is your onboard sound disabled in the bios?

trigg

---

### Post by Recked on 2005-03-27
I have a Sound Blaster Live card. Approx. 4 years old. I looked first in the bios but couldn't locate a spot so disable it. I will check again and see what I can find though.

Seems to be a lot of sound issues with Hoary?

---

### Post by ubuntu-geek on 2005-03-27
[QUOTE=Recked]I have a Sound Blaster Live card. Approx. 4 years old. I looked first in the bios but couldn't locate a spot so disable it. I will check again and see what I can find though.

Seems to be a lot of sound issues with Hoary?[/QUOTE]
 Yeah sound blaster cards in hoary are rough.. I have a bug open..

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6892](https://bugzilla.ubuntu.com/show_bug.cgi?id=6892)

Feel free to reply to it. This might help.. [http://ubuntuforums.org/showthread.php?t=21211](http://ubuntuforums.org/showthread.php?t=21211)

---

### Post by Recked on 2005-03-28
First thanks to you both for the help.

I did some further digging as Trigg suggested and found a entry in the bios which turned out to be the onboard sound. Would have been nice if they just labeled it say something like "onboard sound" but they though it would be more fun giving it a name nobody would think of!!!!!

Anyway the Sound Blaster card is now working just fine.

again my thanks

---

### Post by 1804biker on 2005-04-30
[QUOTE=Recked]First thanks to you both for the help.

I did some further digging as Trigg suggested and found a entry in the bios which turned out to be the onboard sound. Would have been nice if they just labeled it say something like "onboard sound" but they though it would be more fun giving it a name nobody would think of!!!!!

Anyway the Sound Blaster card is now working just fine.

again my thanks[/QUOTE]
 I just installed ubuntu and I am having the same problem.  What, exactly did you do, Trigg?

---

### Post by 1804biker on 2005-04-30
PS...I'm an idiot could be somewhat polite and use the correct name, eh?  What did you do, Recked?  Thanks!

---

### Post by filemanager on 2005-07-03
I'm also having that problem. I found the onboard sound (AC'97 or something) and it is enabled. (It's supposed to be right?) My sound works in WinXP but not in Linux =\

---

