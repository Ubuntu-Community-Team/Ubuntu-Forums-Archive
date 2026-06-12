---
title: "I keep getting error 13 when trying to boot windows"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by vistadude on 2009-05-14
well, it can be hard to explain, but to make a long story short, i have windows 7, windows vista and ubuntu 9.04 on my system, i was using the vista, or i suppose windows 7 boot loader instead of grub on my mbr and everything was working fine, but i started messing around with stuff and i screwed something up. Now thx to super grub i was able to boot windows and linux, but i managed to install grub again though super grub, and i also some how made it so that vista or win 7 would not, but right now i do have grub on my mbr, but heres the problem, now when i try to boot windows though the entry in grub it gives me an error saying "error 13: invalid or unsupported executable format" so now my question would be, how i fix this so i can boot into windows and start using the windows boot loader on my mbr again instead of having grub writen to my mbr

---

### Post by vistadude on 2009-05-15
can anyone please help me, im desperate, i've done all i can think of.

---

### Post by crawdad3 on 2009-05-15
Hi I am sorry I can't help you but maybe you can help me. Did you install windows 7 after vista and ubuntu and did the mbr boot all 3? 
i/m trying to avoid the kind of problems your having but would like to install windows 7 on a 3rd partition just worried about the boot getting messed up Thanks JIM

---

### Post by vistadude on 2009-05-15
yes, i did do that, what i did was i made it so that it used the windows boot loader on the mbr and then installed grub to the partition that linux is installed to, once i did that i added the entry to the windows boot loader so that it will boot linux using grub, and so that when i click on grub it did not show me the grub menu i made it so that grub will not appear, i did most of this thx to a free program called EsayBCD, it let me install the windows boot loader to the mnr and add/modify linux entries on there, that and when u have them set using the windows mnr u can use an other program by the same ppl called ireboot, it makes it so that u click a button and it rebots the computer to that os with out havign to select it from the boot loader on the mbr. both of those programs run in windows only.

you likely wont get messed up like me though, the reason why i got messed up is because i installed windows 7 after vista and ubuntu, and i had it set up fine before, but something removed how ubuntu had grub installed, and its the way i tryed to fix that, i should of just installed grub, but i did a bunch of stuff and that messed me up

---

