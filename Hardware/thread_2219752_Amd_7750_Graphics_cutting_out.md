---
title: "Amd 7750 Graphics cutting out"
date: 2014-04-25
forum: Hardware
---

### Post by neigun on 2014-04-25
Hi 

Just upgraded to Ubuntu Gnome 14.04 from !3.10.

Initially I got the garbled display as per: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1309969](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1309969)

Then I tried a fresh install  and I could then log on, but the card now cuts out after a few minutes/secs.

I've tried the fglrx and updated drivers but still experience the cut out issue.

Any suggestions/solutions?

I had these issues with 13.04 and had to do a lot of tinkering then as well, until 13.10 and this seems a bit of retrograde step.

Neil

---

### Post by nedrerairo on 2014-04-25
not sure if related, but I'd try to reach console with ctrl+alt+f1 to f6 (even if garbled screen), logging in and doing an sudo apt-get update   and then apt-get upgrade to rule out some stuff..  and then reboot.

ctrl + alt + f1 should bring you to tty1 with console login screen presented.

---

### Post by neigun on 2014-04-25
******

---

### Post by neigun on 2014-04-25
Hi Nedrerairo

I've updated the system but no joy.

It's as though the card is overheating. I've read somewhere that by installing fglrx that the cards temperarure dropped, which does not seem to be the case on my system.

---

### Post by neigun on 2014-04-30
Well I tried the Oibaf ppa, which helped for a day and then the cutting out started with a vengeance.

---

### Post by neigun on 2014-11-25
Now on Ubuntu Gnome 14.10 and everything seems OK.

---

