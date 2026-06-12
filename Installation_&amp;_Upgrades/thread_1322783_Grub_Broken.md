---
title: "Grub Broken"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by carterw65 on 2009-11-11
OK here goes. I dual boot with XP. When I upgraded from 9.04 to 9.10 I used my old menu.lst so my sound was broken. So, I updated my grub to grub2 to make sure I booted into the 9.10 kernel and it fixed the the sound and upon startup gave me the grub menu. This worked once.

I rebooted to go into XP and grub gave me an error 15 and would not boot into anything. So I got out the old trusty Supergrub cd to try to fix the porblem. Long story short, the computer now boots directly to XP. To get to 9.10 I have to use the Supergrub cd.

Can anyone please lead me in the right direction to fix this?

Thanks a million!

---

### Post by frodon on 2009-11-11
You should find all you need there:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by carterw65 on 2009-11-11
That got me in the right direction. I ended up reverting back to legacy grub and it is working. Not sure what I will do from here. I will need to read up on grub2 before I try anything with it. Lesson learned: use the new menu.lst and if it breaks your dual boot, just fix the menu.lst. Not sure how that works with grub2 though. Documentation says it no longer uses menu.lst.

Thanks!

---

### Post by Rodney9 on 2010-12-17
If only the word "Grub" appears at the top of the screen without a prompt (access to the command line) or menu, refer to the [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") section.

---

