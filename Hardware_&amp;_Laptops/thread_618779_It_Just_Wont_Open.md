---
title: "It Just Wont Open"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by geralz on 2007-11-20
I just installed ubuntu in my laptop today. A friend of mine who loved it helped me installed it. The problem is that everytime we put the name and password correctly it restarted and open the same asking for the name and password again and again we put the name and password liki 7 times and each time it just reopened can someone help us by the way my laptop has windows vista just in case.

---

### Post by nick_h on 2007-11-20
If you switch to a terminal using CTL+ALT+F1 can you login OK?

---

### Post by Fran89 on 2007-11-20
I'm his friend, let me specify. I installed Ubuntu Gutsy in my computer and it runs excellent, so he had Vista and I recommended Gutsy, the first thing i noticed is that during the installation, it did not detect Windows Vista as it has with other laptops I've installed before, and the live CD did not boot correctly , it went into Gnome but then in an instant it returned me to a login screen and said: User Ubuntu will log in in 30 seconds, but when the time was up... it turned off the screen and then returned me to the login screen. so I decided to use the Altenate CD, an so I did, it installed flawlessly but the same thing happened here. once inside Gnome it returned me to login screen. How does vista run? I edited the /boot/grub/menu.lst to be able to boot Vista, How i edited it? It seems Ubuntu can run ok in Failsafe terminal, and from there it was just ```
sudo nano /boot/grub/menu.lst
```, but its strange that it wont boot GNOME, can anyone shed light on this, BTW its an Acer Aspire 3100 notebook, my freind forgot to metion that. so anyone else experience this? ive installed this on a Gateway ML3607 and apart from no sound it runs flawlessly alongside Vista so I did not think is this... Help please.:confused:

---

### Post by nick_h on 2007-11-20
Have you tried looking at the logs for any error messages?

/var/log/Xorg.0.log might be a good place to start.

---

### Post by Fran89 on 2007-11-20
> **nick_h said:**
> Have you tried looking at the logs for any error messages?

/var/log/Xorg.0.log might be a good place to start.

hmm i would check it out but im not there anymore, and he doesnt know how to work the terminal, ill have to check it out tommorow, i doubt its that type of error

---

### Post by Fran89 on 2007-11-21
I managed to open it in Gnome Failsafe... weird,  but it had 2 restricted drivers, one for the chipset and one for the ATI, any ideas.. ill install them if nothing else comes up

---

