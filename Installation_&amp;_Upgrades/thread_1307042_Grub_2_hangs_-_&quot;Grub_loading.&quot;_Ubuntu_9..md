---
title: "Grub 2 hangs - &quot;Grub loading.&quot; Ubuntu 9.10."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by berman56 on 2009-10-30
I just did a fresh install of 9.10 on my HP nc6400 laptop.  I dual boot with Win XP.  I've been running Ubuntu and XP side-by-side for a long time without trouble.  After installation of 9.10, the computer hangs at "Grub loading." and goes no further - ie. it never gets to the grub menu (I've left it for a few hours and nothing).

 Interestingly, if I reinstall Ubuntu, it allows me to boot successfully once.  And then the problem recurs.

I would greatly appreciate any help!!!

Thanks.

---

### Post by berman56 on 2009-11-03
I realized this problem is an "Undecided" BUG in launchpad:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

At least I'm not the only person having this problem.  A somewhat complicated workaround is suggested in the discussion but I am too scared to give it a go.

Oh well, 9.04 for now.

---

### Post by berman56 on 2009-11-04
A user in the launchpad BUG discussion solved the problem for me:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

I dual boot Ubuntu with Windows XP on an HP laptop (nc6400).  Turns out that HP software appears to mess with MBR each boot and this trips up GRUB2.  I uninstalled HP protecttools and HP recovery manager installer (unfortunately I didn't do this systematically and I don't know which is responsible) and then did a clean installation of 9.10 and everything works perfectly.  No further GRUB2 trouble!!!:p

---

### Post by PhoneixS on 2009-11-11
> **berman56 said:**
> A user in the launchpad BUG discussion solved the problem for me:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

I dual boot Ubuntu with Windows XP on an HP laptop (nc6400).  Turns out that HP software appears to mess with MBR each boot and this trips up GRUB2.  I uninstalled HP protecttools and HP recovery manager installer (unfortunately I didn't do this systematically and I don't know which is responsible) and then did a clean installation of 9.10 and everything works perfectly.  No further GRUB2 trouble!!!:p
Thank you for the info.

---

### Post by s_raghu20 on 2009-11-11
Incidentally, my HP Compaq 6710b (with Vista Business) did not face any such issues during the upgrade.

Also, my home PC (self assembled - no branding) did not face any issues either.

should I be happy (that everything was fine) or should I worry more since it wasnt reported ? :D

---

### Post by jwj12001 on 2010-01-16
I had exactly the same problem with my HP desktop and dual booting. If I booted into XP, next time Grub would hang. Uninstalling the HP recovery software fixed it. Thanks for the tip.

---

