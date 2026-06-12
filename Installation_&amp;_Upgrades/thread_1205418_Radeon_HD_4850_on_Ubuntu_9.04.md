---
title: "Radeon HD 4850 on Ubuntu 9.04"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by WoodbineG on 2009-07-06
Whats shaking bros?

This is my second shot at Ubuntu, about a year ago I tried to install Ubuntu 7.10 and ran into some issues in other words complete failure :cry:. This weekend my uncle had some issues with his XP based laptop which I fixed by installing Ubuntu 9.04 (kudos for me) and so I re-fell in love with Ubuntu and now I want Ubuntu Studio 9.04 on my PC. I'm originally a gamer and my PC has an HD4850, I've heard of people having issues with drivers and stuff and I want to get an answer on whether can I run Ubuntu 9.04 with my HD4850 or not.

Help a bro out please and thanks for your time! :p

---

### Post by X-BANE on 2009-07-06
You should be able to, but ATI's Linux drivers are notoriously bad.

---

### Post by WoodbineG on 2009-07-06
> **X-BANE said:**
> You should be able to, but ATI's Linux drivers are notoriously bad.

Okay so what drivers should I use?

---

### Post by X-BANE on 2009-07-06
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-6-x86.x86_64.run)

---

### Post by WoodbineG on 2009-07-06
> **X-BANE said:**
> [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-6-x86.x86_64.run)

And how am I supposed to open that?

---

### Post by WoodbineG on 2009-07-06
Bump!

---

### Post by automaton26 on 2009-07-06
I'm using this card with no problems at all - there's a pdf available from ATI which describes how to install & uninstall once you have downloaded the .run file:

To **install** the driver package (use the latest N-NN version):
```
sudo sh ./ati-driver-installer-9-8-x86.x86_64.run
sudo aticonfig --initial

```

To run the ATI **Catalyst Control Center** (ccc):
```
amdcccle
```

To **uninstall** the driver package:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh

```

Please bear in mind that a lot of older cards were no longer supported after version 9.3, so you might need to _either_ try that version instead (*only* under Ubuntu 8.10) _or_ wait & hope that later versions of Ubuntu have default Open Source drivers that provide decent 3D acceleration.

---

### Post by lunarmelody on 2009-07-07
> **automaton26 said:**
> I'm using this card with no problems at all - there's a pdf available from ATI which describes how to install & uninstall once you have the .run file:

To **install** the driver package:
```
sudo sh ./ati-driver-installer-9-6-x86.x86_64.run
sudo aticonfig --initial

```

To **uninstall** the driver package:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh

```


Thanks for the instructions.  I've got the drivers running with my ATI HD4670, which is good.  However, once they're installed, how do you configure the display?  By this I mean, how do you change the screen resolution?  The drivers auto-set way too low, and using the built-in settings (System -> Preferences -> Display) doesn't work.  If I change the settings in this box, I'm told to log out and log back in again, only nothing has been changed.  Am I missing something?  Thanks!

[EDIT]  I found the ATI Catalyst Control Center, so I can fix all of that now.

---

### Post by ThinkMud on 2009-07-09
I had the same issues with the system>prefs.>dislplay not working at first too.  what I did to fix this was go through the ATI's "unofficial wikki" here: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")  and then rebooted and everything seemed to work good.  I have dual monitors one that is a 24" wide screen 1900x1200 and one that is a dell 1600x1200 and I have both working now.

only down side is that I am still not getting half of the graphic quality out of this card (ati radeon hd 4850), but hopefully I can tweak that later once I learn more about it all.

Good luck!

---

### Post by WoodbineG on 2009-07-10
I just wanted to thank everyone for helping me out, I got the drivers installed and my PC runs beautifully flawlessly.


Thanks for your time guys! highly appreciated  ):P

---

