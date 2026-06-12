---
title: "Karmic on Thinkpad R51 Radeon RV250 white screen"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by openBA on 2009-11-08
Hi all,

after a fresh install on multiboot ( Ubuntu 8.04, 9.04, XP) Thinkpad R51 with Radeon M 9200 (RV250) I can login only to the "white desktop" with live mouse cursor. (similar to [http://ubuntuforums.org/showthread.php?t=1302158&highlight=white+screen+radeon](http://ubuntuforums.org/showthread.php?t=1302158&highlight=white+screen+radeon)). 

Funny thing is, that Karmic live-CD is able to get to desktop, but installed one doesn't! But live-CD will totally freeze as I try to resize some windows, or start some applications. CD check was OK, also other live distro's (Knoppix 6.1,..) and also other OS's are working, so it's not a hardware problem. 

What I tried without luck:
- second fresh install this time with EXT4
- apt-get update/upgrade in text console
- envyng -t 
- created xorg.conf and checked some different settings for open radeon driver (even VESA)
- added KDE desktop, same white

IMHO it it's a game-stopping bug in Karmic for a plenty of older PCs. Please could you kindly help to a regular Ubuntu user (not guru).

---

### Post by openBA on 2009-11-08
follow up:

After removing Thinkpad R51 from docking station (multi display), I installed Karmic for the third time and now I'm able to login to the desktop (without white screen), but now I have similar freezes as with LiveCD. I did note that radeon/X driver was very bad at windows redrawing. So I suspect that some X settings for RV250 are not optimal or is something wrong with open source radeon (kernel) drivers.

Any proposal what should be done ?

---

### Post by openBA on 2009-11-09
just installed Fedora Core 12 (RC) with similar kernel and radeon driver and it works! No reproducible crashes. So it seems it is Ubuntu 9.10 problem. 8.04 and 9.04 are still working nicely on the same notebook.

---

### Post by openBA on 2009-11-10
Mandriva 2010 (Kernel 2.6.31.5, Mesa 1.3  7.5.2 ) is working even better then FC 12 RC on the same laptop.

Even external monitor handling works, hibernate and suspend also. Very nice.

But I would prefer Ubuntu 9.10. Any idea, how could Karmic Koala be friendly to my Thinkpad R51? Anybody?

---

### Post by openBA on 2009-11-22
Third try - success !

Before first gnome log after Karmic installation, I have done upgrade in terminal mode. It seems, that the latest upgrades are correcting my radeon RV250 problems. After a day of work,  there was no crash and everything seems to work.

Congratulations to Ubuntu and Debian teems. Thanks!

---

