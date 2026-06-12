---
title: "External monitor problem Ubuntu 10.04 ATI HD2400XT"
date: 2011-03-22
forum: Hardware
---

### Post by insecure hyena on 2011-03-22
Hi everyone I write this post after a long unsuccessful search on the Web.
My problem is that whenever I plug in an external monitor on my laptop I get that both the screen, the external and the internal one, become "unreadable". They simple mess up causing the hanging up of the entire system. The only thing that I can do when this happen is to manually shutdown the PC by pressing the power button.
Actually I'm using Ubuntu 10.04 LTS on an Acer Aspire 4920g notebook that ships an ATI HD2400XT graphic card.
The driver that I've installed are the latest proprietary downloadable from the official site of AMD.
A note: a few month ago, always using Ubuntu 10.04 LTS and the driver installed through the Ubuntu utility (the one that automatically detect and install the proprietary driver) there was no problem by attaching external monitors.
So at the end I'm asking help to the community to solve this big issue. In fact I often use external monitor to work.

---

### Post by insecure hyena on 2011-03-22
guys...c'mon...UP!!! HELP!!!

---

### Post by insecure hyena on 2011-03-23
Is there really nobody that have the same problem I've exposed over here??! C'mon community help a poor novice of the Linux world!!!

---

### Post by insecure hyena on 2011-03-24
Up

---

### Post by insecure hyena on 2011-03-28
nth's UP...c'mon guys help a poor novice!!!

---

### Post by insecure hyena on 2011-03-29
Ok guys I marked this post as solved...but hey...I've done this all alone :)!!!
Simply I added to my repo the this ppa:
"https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"
I added it utilizing Ubuntu Tweak. Yes I know this could be done also by typing a few command in a terminal window but hey I feel comfortable with Ubuntu Tweak (i prefer to use a mouse than a keyboard...I'm just joking XD).
However after updating the system the problem is gone.
So simply "sudo apt-get update" and then "sudo apt-get distupgrade".
Hope this could help people having the same problem I had in this last days.
;)

---

