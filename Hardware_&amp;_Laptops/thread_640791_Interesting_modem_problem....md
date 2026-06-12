---
title: "Interesting modem problem..."
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by koleoptero on 2007-12-14
I have a problem with my adsl modem in kubuntu (and all other kde based distros). My modem is he fabled crappy sagem fast-800 and here's what makes my problem interesting: I used the ueagle drivers that as far as I know are open source, and a guide that I found (written in Greek so I won't post link) to setup my modem. In short you copy all the files needed for the pc to recognize the modem in /lib/firmware/ueagle-atm. All the times I do that and connect the modem it shows to be working (detecting and synchronizing with the adsl, something like that). Then I create a connection manually by doing the following steps:

1. I create a file /etc/ppp/peers/ueagle-atm that contains:

```
user "username"
plugin pppoatm.so VC.VP
noipdefault
usepeerdns
defaultroute
persist
noauth
```

Where I replace the username with my username and VC.VP with 8.35 as I should.

2. I edit /etc/ppp/pap-secrets and /etc/ppp/chap-secrets and add a line with my username and password

```
"username"  "*"  "password"  "*"
```

3. I dial using ```
pon ueagle-atm
``` or in kubuntu ```
pppd call ueagle-atm
```


Here's the funny thing now. In Ubuntu and Xubuntu this works like a charm. It connects and everything works fine. In Kubuntu though it does not. It connects and nothing finds anything. I checked with some commands (I don't remember them atm) and saw that my computer had indeed established the connection, had acquired an IP, has successfully detected the DNS servers it should, it just didn't open any site and no other program (IRC, MSN, torrents) could connect to the network.

So... is there something that can be done? I really wanted to try out kubuntu cause I like kde. And the problem is I can't even use some other distro with KDE, the problem seems to be something kde-specific (since gnome and xfce didn't have any problems). Isn't it weird that the desktop environment can cause such a problem?

Anyway I hope someone has some idea what to do. I'll use the live cd to check if it works.

EDIT: I posted this in this part of the forum cause I have a laptop (toshiba satellite m70). If it should go anywhere else, please move it.

---

### Post by koleoptero on 2007-12-15
bump...:neutral:

---

### Post by koleoptero on 2007-12-15
bump #2... :(

---

### Post by koleoptero on 2007-12-16
last one.... bump 3...:frown:

---

### Post by kodak on 2007-12-18
hi i will get back to in moment on this.

---

### Post by kodak on 2007-12-18
have you unplugged your modem then wait a few seconds and plug it in again then installing the driver?

---

### Post by koleoptero on 2007-12-18
> **kodak said:**
> have you unplugged your modem then wait a few seconds and plug it in again then installing the driver?

yeap, have tried all that. The modem worked under ubuntu. Kubuntu is the problem...

---

### Post by kodak on 2007-12-18
> **koleoptero said:**
> yeap, have tried all that. The modem worked under ubuntu. Kubuntu is the problem...

It's been a while since i was in a KDE machine, it was Mandriva and worked fine with eagle driver.

have you set up the connection in the control center?

---

### Post by koleoptero on 2007-12-21
I tried to do that too, no results. I also tried another guide I found somewhere here (don't remember the link) that used the ueagle drivers that are included with the live cd. No results there either. It looks like I'll have to stay away from kde after all :(

And I really wanted to be able to use amarok and the rest of kde's programs in their native environment... :(

---

