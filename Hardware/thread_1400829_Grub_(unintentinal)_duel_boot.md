---
title: "Grub (unintentinal) duel boot"
date: 2010-02-07
forum: Hardware
---

### Post by jc4orr on 2010-02-07
I re-installed UBUNTU 9.10 Yesterday morning because it bricked on me, and that was the easiest way to get everything to work again. but back to the main point, when it updated itself with all the new updates, I had my windows hdd plugged in, because I was transferring all of my music, videos, ect. over to the UBUNTU HDD. well, when ubuntu restarted, grub came up and gave me the option of booting windows. I want it to boot directly into ubuntu, I know there is a way to tell it to do that automatically, but I dont know what file I have to edit in grub. 
could someone tell me what I have to change, and what it should be changed to?

---

### Post by efflandt on 2010-02-07
Did you try **sudo update-grub** without the external drive connected?  If that still comes up with grub menu, see /etc/default/grub.  But you need to edit that to zero as root (**sudo nano** or **gksu gedit**).

See [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) for some /etc/default/grub parameters.  After editing you have to do **sudo update-grub**.

---

### Post by jc4orr on 2010-02-07
thanks for the quick response, Ill give that a try and let you know if that fixed the problem.

---

### Post by jc4orr on 2010-03-02
> **efflandt said:**
> Did you try **sudo update-grub** without the external drive connected?  If that still comes up with grub menu, see /etc/default/grub.  But you need to edit that to zero as root (**sudo nano** or **gksu gedit**).

See [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) for some /etc/default/grub parameters.  After editing you have to do **sudo update-grub**.

I did this and forgot to post my results. it worked great, and I dont have a problem anymore. thanks for the help.

---

