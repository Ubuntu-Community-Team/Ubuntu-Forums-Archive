---
title: "Partian upgrade (I think)  and resolution completely Effed"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by osabr22000 on 2009-02-24
I was running Ubuntu 7.10, then I believe I tried to upgrade.  First, I tried upgrading through the automatic option offered through the OS, but I have Hughesnet as my ISP and that definitely would fapped me so I canceled it once I saw the size of the download.  After I tried to upgrade then cancelled, I would have resolution problems with my display (it's a laptop) right at start up.  My screen is a 15.4" widescreen, however, sporadically it would think it's a standard/square display and leave a blank strip on the right side of the screen.
Later on, I purchased a cd of Ubuntu 8.04 and tried to upgrade.  It appears though that, the cd is damaged.  When I tried to ugprade with that cd a few months ago, the system would not upgrade from the cd when I booted into Ubuntu from the hd.  I also tried to do a live boot with that disc (on two different systems) and was not successful.  Then, I actually tried to do an install from that same disc and wasn't successful.  After that... the resolution problem went from a sporadic problem to a constant problem.
I decided to give up on upgrading at the moment and just wanted to fix the resolution issue.  Sources I found said that it occurs because I didn't have the proper driver from ATI installed.  It also said that problem usually arises when you cancel an upgrade.  I found what I thought was the proper driver, but couldn't install it.  I also read somewhere that upgrading Ubuntu can fix the problem.  So I tried that.
Then next thing I did was go to a free hotspot, and do the auto upgrade offered through the OS online.  I let the whole update complete, and now, I cannot even start an instance of Ubuntu properly now.
Before the  upgrade, GRUB 1.5 offered these options:
Ubuntu 7.10
Ubuntu 7.10 safe
Ubuntu 7.10
Ubuntu 7.10 safe
Memtest 86
Other OS
XP Home

I could only boot into the top instance for Ubuntu...long story.
After the upgrade this is what GRUB offers me this:
Ubuntu 8.04
Ubuntu 8.04 recovery
Ubuntu 8.04
Ubuntu 8.04 recovery
Ubuntu 8.04
Ubuntu 8.04 recovery
memtest
Other operating systems
XP home
Ubuntu 7.10
Ubuntu 7.10 recovery

When going into 7.10, I am only given the option for low graphics mode.  Is it possible for me to fix the resolution and upgrade this?
Thanks in advance.

---

### Post by osabr22000 on 2009-02-25
Here's a quick update:  This morning I tried again, and I tried the recovery option.  It actually booted into Ubuntu, I got something that had said about 5 or 6 different programs crashed.  So it appears that the first problem is fixed, but I still have that problem with the resolution.  Does anybody know how to solve this?  Thanks.

---

### Post by osabr22000 on 2009-02-25
Another update.  After I've used the recovery option in GRUB, should I be able to access and boot that partition with the regular option?  Because I can't, I still have to use recovery... Anyone??

---

### Post by osabr22000 on 2009-02-28
Have I posted this in the correct section??

---

### Post by dixonstalbert on 2009-02-28
it sounds like the X graphics system is not configured correctly.

If you can get into recovery mode, try the command 

```
dpkg-reconfigure xserver-xorg
```

this should start a menu system that allows to set up your ati graphics driver.

If that doesnt work, see what files are in the /etc/X11 directory - you might have a backup copy of your xorg.conf file that works.
Rename your current xorg.conf file and rename one of the backups xorg.conf and reboot.

good luck. ati drivers are a real pain!

---

