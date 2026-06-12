---
title: "Running slow/freezes all of a sudden"
date: 2008-10-15
forum: General Help
---

### Post by mulle12 on 2008-10-15
Hi! 2 days ago, i installed Ubuntu 8.04 as my main and only OS. It works like a charm, looks really nice and i configured it a bit to "fit my needs".

Now, all of a sudden, it starts to run slow, lagging and some programs(firefox mostly) needs to be forced to quit. When i run CTRL+ALT+BACKSPACE, nothing happens. I see my wallpaper and mousepointer. No menus or icons. I don't know if this issue started after the update that ran earlier today, or before.

What may be the problem?

Spec:

AMD Athlon 3500+
ATi X1950XT 256mb
2048mb RAM
Creative SoundBlaster LIVE!
Maxtor 160gb IDE-harddrive
Maxtor OneTouch4 500gb USB-harddrive


Hope you guys can help me, thanks!

---

### Post by geirha on 2008-10-15
Try booting with the previous kernel and see if you get the same symptoms.

---

### Post by mulle12 on 2008-10-15
> **geirha said:**
> Try booting with the previous kernel and see if you get the same symptoms.

Do i change kernel in the GRUB menu? In that case, i rebooted my computer, booting with the 2.6.24.19-generic, i believe. Or at least it ended with 19.

I believe this works better. Is there any way i can choose this kernel to be "standard", and that Ubuntu shall always boot from this kernel?

---

### Post by geirha on 2008-10-15
Yes, when the grub-menu shows up in the early boot stage, you select the third entry (most likely) to get the previous kernel, 2.6.24-19. You can make it default by changing the default variable in /boot/grub/menu.lst, but that will just postpone the problem.

Have you installed any drivers from outside the ubuntu repositories?

I'd recommend you report the problems you have with the latest kernel at launchpad.net, that way they should be able to find and fix the bug if it is indeed a bug in the newest kernel, and a new kernel update should be right around the corner.

---

### Post by mulle12 on 2008-10-15
> **geirha said:**
> Yes, when the grub-menu shows up in the early boot stage, you select the third entry (most likely) to get the previous kernel, 2.6.24-19. You can make it default by changing the default variable in /boot/grub/menu.lst, but that will just postpone the problem.

Have you installed any drivers from outside the ubuntu repositories?

I'd recommend you report the problems you have with the latest kernel at launchpad.net, that way they should be able to find and fix the bug if it is indeed a bug in the newest kernel, and a new kernel update should be right around the corner.

Hmm, i don't know about the drivers to my graphicscard.

I reported the problem at launchpad.net as you said, hope a solution will come soon!

Thanks for the help! I edit/bump if i get more info about the problem. :)

---

