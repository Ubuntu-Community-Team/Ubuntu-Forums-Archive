---
title: "Ibm R40"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by Omnimon on 2007-01-24
Hi, I have a IBM R40.... 

I originally have Windows XP and I just did a fresh install of Ubuntu 6.10 [i didn't let it partitioned] and when i tired to boot up, IT CRASHED WITH grub17 error. i looked at other post but i couldn't understand "grub" commands. Is there anything I can do? I can load into the live CD mode

---

### Post by swerner on 2007-12-05
Works fine for me, but I don't try dual boot with XP.  See [here]("https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR40-2681") on all the details of getting the R40 all set up:

---

### Post by monkeyking on 2007-12-20
I've spend 30 hours trying to get the r40 to dual boot with xp.
And I think it's impossible.

I think the the bios reserves some speciel mbr for the ibm helpstuff, which grub doesn't know how to send to windows xp.

---

### Post by swerner on 2007-12-20
When I first got my R40 a few years ago, I did have dual boot working well.  One thing which is different is that I used LILO instead of Grub, but I don't know if this would be a satisfactory solution.  I have also removed the hidden IBM partition.

Can you mount the Windows XP partition from Linux? What about upgrading to Ubuntu 7.10.

---

