---
title: "Not possible to go back from 9.10 to 9.04"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by luigifonti on 2009-11-12
I had Ubuntu 9.04 on my laptop, together with Windows Vista in a different partition. Grub loader allowed the choice at boot time.
Now I have installed Ubuntu 9.10, and grub has been replaced with grub2.
Ubuntu 9.10 has some problems (internet key not working, android sdk not working, and more...), so I tried to reinstall Ubuntu 9.04
At the end of the installation process, I got a problem: it is no more possible to install the old grub on the hard disk: the installation process gives an error. I retried again, with the same result.
Somebody can help me ?
Luigi Fonti

---

### Post by MartinEve on 2009-11-12
I'm afraid I can't give any detail on the process, but [http://en.gentoo-wiki.com/wiki/Grub2](http://en.gentoo-wiki.com/wiki/Grub2) suggests that it should be possible (even easy) to downgrade from grub2.

---

### Post by audiomick on 2009-11-12
Another viewpoint:
The problem you had was with 9.10, not with grub. Maybe you can stay with grub2, and then you would only have to reconstruct the grub file, not try and downgrade. It's only a guess, but it might be worth a thought...

---

### Post by coffeecat on 2009-11-12
The presence of grub2 is not the reason you are getting an error when you try to install Ubuntu 9.04. The remnants of grub2 will simply be overwritten with legacy grub by the Jaunty installer - there is nothing that grub2 code can "do" because it is not being invoked. It's just like any other code or file written to a hard disc.

There is clearly a problem with the 9.04 installation because you are getting an error message. But what was the error message? You do not tell us. Without that, there are not many constructive suggestions that anyone can make.

---

### Post by luigifonti on 2009-11-13
What I get at the end of the 9.04 installation, is a very simple and generic error message:

FATAL ERROR - The installation of grub failed.

At that point I can't boot any system from hard disk

Luigi Fonti

---

