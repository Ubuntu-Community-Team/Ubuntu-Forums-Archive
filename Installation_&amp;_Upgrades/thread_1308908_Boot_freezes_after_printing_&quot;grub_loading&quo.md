---
title: "Boot freezes after printing &quot;grub loading&quot;"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by lorentzr on 2009-11-01
I have a dual boot HP desktop that until yesterday could boot either Feisty Fawn (or some similarly old release) or XP professional. I did a clean install of 9.10 over Fesity. It booted to Ubuntu fine and a shutdown and reboot to 9.10 also worked fine. But after booting to XP and then restarting the machine it freezes after printing "grub loading". Just in case, I resinstalled 9.10 and got exactly the same behavior. The only thing that makes any sense is that XP does something to grub, but it never happened when I had Feisty running.

Since I needed to do some Windows work, I reinstalled 9.10 yet one more time, booted up to XP but now I can't turn off the machine since I'm pretty sure if I do the same thing will happen and I won't be able to boot to anything until I reinstall 9.10 yet another time.

Does this sound familiar to anybody else, and much more interesting, anybody have any suggestions to help me out?

Thanks!

---

### Post by phekdra on 2009-11-01
> **lorentzr said:**
> 
Does this sound familiar to anybody else, and much more interesting, anybody have any suggestions to help me out?


Very familiar - I've been having exactly the same problem - see here:

[http://ubuntuforums.org/showthread.php?t=1307401]("http://ubuntuforums.org/showthread.php?t=1307401")

Andrew

---

### Post by lorentzr on 2009-11-09
If you're using an HP machine, the solution is probably here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

