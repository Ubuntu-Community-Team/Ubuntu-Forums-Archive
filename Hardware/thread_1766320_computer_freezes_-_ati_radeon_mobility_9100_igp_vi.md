---
title: "computer freezes - ati radeon mobility 9100 igp video card"
date: 2011-05-24
forum: Hardware
---

### Post by farchumbre on 2011-05-24
Hi

I am using an old toshiba satellite with a radeon mobility 9100 igp video card.
I recently install xubuntu 11.04 and the computer freezes at random times (the keyboard and the mouse stop responding and the only way out is a restart).
I tried to uninstall fglrx drivers, reinstall the ati drivers without success.
I install ubuntu 11.04 and I also tried lubuntu 11.04.
So far nothing helped.
Does anyone know what could be causing the problem?

Thanks

---

### Post by mastablasta on 2011-05-24
overheating or bad capacitors on motherboard. it definatelly seems like hardware issue.
 
though it would be good to know if any other system run with no issues. then it's either bad driver (but for this old card they should be ok by now) or again overheating. for overheating try to "spray" the holes with some compressed air.
 
you can't install ATI proprietary drivers with this old card. if you did that and then experienced the crahses that would explain a lot.

---

### Post by farchumbre on 2011-05-24
Hi
The computer worked fine under windows xp 2 days ago.
The funs and the heat sink were cleaned two weeks ago and it is not overheating.
I did not install the ATI proprietary drivers since jockey is not showing any to install.
Where can I find those drivers?
The random freezing seems to be an issue with ati radeon old cards.

Thanks

---

### Post by mastablasta on 2011-05-25
opensource drivers are installed by default (it's what gets your picture up there).
 
you might have some luck using a testing version of the drivers (but please read the instructions and notes  before you do this):
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
 
You didn't mention what Ubuntu version you are using.
also have a look here for more information (and links): [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by farchumbre on 2011-05-25
THANKS

I tried the 10.04 and the 11.04 versions of ubuntu, unity 2d, xubuntu and lubuntu.
All of them show the same problem. The keyboard and mouse freeze at random times.

---

### Post by farchumbre on 2011-05-25
I tried already [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
but it didn't help. I will try the ppa.

---

### Post by farchumbre on 2011-09-26
I disabled from the bios the serial connector and it worked

---

