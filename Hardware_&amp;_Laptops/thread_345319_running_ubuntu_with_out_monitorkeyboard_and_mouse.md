---
title: "running ubuntu with out monitor/keyboard and mouse"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by dysolve on 2007-01-24
Hello All,
 I am currently build a basic web/mail server at home. But I want to hide my ubuntu box in a cupboard. there is not enough room to include the monitor and keyboard with it. So I set-up VPN and that works great. But after moving the computer and logging in with vpn the screens res is set to 640*480 and Its impossible to use via VPN. My question is how do I make the computer think it has a monitor attached or for it to display the screen res it would with the monitor attached
thanks in advance
David.

---

### Post by renzokuken on 2007-01-24
Can't you use SSH for this sort of thing?

---

### Post by dysolve on 2007-01-24
no matter what "VPN" software I use i am stuck with 320*230 res.. I have found if I boot the machine up with the monitor attached it works fine, but if it boots up with monitor off or not attached the res goes to 320

---

### Post by renzokuken on 2007-01-24
Have you checked the xorg.conf on your server and checked the listed resolutions in there (I'm assuming your server has X installed)

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by dysolve on 2007-01-24
ok i will rephrase the question. can i make it so when my machine boots up without the monitor attached it uses the conf file as if the monitor was attached?

---

