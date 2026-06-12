---
title: "Can't get to Ubuntu GUI/GNOME on startup, I only get a Bash prompt HELP!"
date: 2011-03-23
forum: Hardware
---

### Post by mcavoybn on 2011-03-23
Ok.. this is VERY embarrassing, but last night, in an effort to fix some issues running steam games ([http://ubuntuforums.org/showthread.php?p=10586171#post10586171](http://ubuntuforums.org/showthread.php?p=10586171#post10586171)) I installed a new ati catalyst driver (Radeon HD 4200) manually by downloading the x86 linux driver from the ati website. I installed it, and figured that it would all go down smoothly, but it didn't.

My wobbly windows weren't working (SHUT. DOWN. EVERYTHING.) and the desktop switcher cube, and just about everything from the CompizConfig settings refused to work the way it should. Also, alot of default Ubuntu GUI things weren't working right, so I knew something went horribly wrong with the new driver I installed.

The right drivers are installed, everything was checked and good and the way it should be, but still nothing worked. I decided I must delete one of the 2 catalyst drivers I installed.

This is where everything went wrong. I deleted it by typing:
```

sudo sh /usr/share/ati/fglrx-uninstall.sh
```
It ran, and I rebooted, and now all I get is some sort of Bash/Terminal prompt on startup. It asks me for my username and my password, but there is no GUI/GNOME in sight.

I tried reinstalling the drivers from the low-graphics recovery mode, and it all worked 100% fine, but now I have 2 catalyst managers in my system>preferences, and I also tried activating the driver through system>administration>additional drivers, but it does not work, an error message pops up and says I need to look at /var/log/jockey.log, which I couldn't make any sense of.

Please, help. Where do i go?/What do i do? 
Can I not activate the drivers in recovery mode? That just seems silly.

Thanks- mcavoybn

---

