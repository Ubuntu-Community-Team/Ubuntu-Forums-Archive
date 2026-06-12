---
title: "resizing the linux partition"
date: 2008-09-18
forum: General Help
---

### Post by twitch2197 on 2008-09-18
would it be safe for me to resize the ubuntu partition from windows, using the partitioning tool?
i'm not quite comfortable with doing things like that from the terminal, otherwise i'd resize it from there.
the reason i ask is i'm unsure if i'll need to resize the swap partition and the main ubuntu one as well. could someone tell me what i CAN and CAN'T do? i know from past experience that i can't just delete the linux part, cuz it'll corrupt the bootloader.

---

### Post by Alfx on 2008-09-18
You CAN delete the linux partition from windows or anything.

Then you boot from your windows CD, ask for repair then write "fixmbr"(without the quotes)

That will re-install the original windows loader.

---

### Post by oilchangeguy on 2008-09-18
> **twitch2197 said:**
> would it be safe for me to resize the ubuntu partition from windows, using the partitioning tool?
i'm not quite comfortable with doing things like that from the terminal, otherwise i'd resize it from there.
the reason i ask is i'm unsure if i'll need to resize the swap partition and the main ubuntu one as well. could someone tell me what i CAN and CAN'T do? i know from past experience that i can't just delete the linux part, cuz it'll corrupt the bootloader.

you don't use the terminal to resize a partition. you use gparted, or the partition manager. and if you can see the ubuntu partiton from windows you should be able to do it there as well. and just resize the "main" ubuntu partition.

---

### Post by twitch2197 on 2008-09-18
okay thanks. as you can tell i'm pretty much a total newbie to linux

---

### Post by louieb on 2008-09-18
> **twitch2197 said:**
> would it be safe for me to resize the ubuntu partition from windows, using the partitioning tool?...

If you mean the one that comes with VISTA. The answer is NO.
 
I've heard commercial programs such as partition magic can resize an ext3 (the default Ubuntu) partition.

I use and recommend the open source program GParted. It is best to run it from a live CD. I use the  [SystemRescueCd.]("http://www.sysresccd.org/Main_Page")

[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 

Here a good read on what you can and can't do [HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018")

---

### Post by twitch2197 on 2008-09-19
well all my problems (resizing partition, touchpad not working) have been solved. my grub got corrupt (while trying to resize i screwed it up, which in turn fixed it... how ironic) so i just reinstalled linux over the whole computer. i had nothing to lose on my vista anyway...

---

