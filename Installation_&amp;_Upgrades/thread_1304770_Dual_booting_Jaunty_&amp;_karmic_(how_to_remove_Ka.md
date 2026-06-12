---
title: "Dual booting Jaunty &amp; karmic (how to remove Karmic &amp;  give the space back to jaunty"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by dj-toonz on 2009-10-29
Hi all, Just found out by my mistake after dual booting Jaunty & karmic (while installing Karmic) that the 3G HSDPA modem bug hasn't been fixed yet :( & can't update or even use the internet under the Karmic Partition (only Jaunty) so what I want to do is totally remove Karmic from the laptop & go back to single booting Jaunty. How do I do it & give the space back to Jaunty after removing Karmic & put grub back to normal ? cheers

---

### Post by utnubuuser on 2009-10-29
Insert  liveCD, not 9.10, - once at the desktop, start gparted from System>>Administration>>Partition Editor, right-click your Karmic partition(s), unmount them, then choose delete from the menu,  then right-click your 9.04 partition, unmount, then select resize, in the pop-up menu resize, then click apply.

then:> [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

