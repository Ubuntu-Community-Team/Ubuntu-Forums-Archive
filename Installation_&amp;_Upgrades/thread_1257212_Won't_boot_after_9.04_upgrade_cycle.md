---
title: "Won't boot after 9.04 upgrade cycle"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by tb56 on 2009-09-03
I installed a fresh version of Jaunty on a Toshiba laptop. Everything worked fine. Of course, the update manager came up and listed tons of updates to be installed. Installed all updates. Hit 'RESTART'. Will not boot. Only comes up with Toshiba splash screen then cursor in top left corner. I am now reinstalling. Any clue on which update could have caused the problem? Perhaps a kernel update? How can update required systems without this problem recurring?

Thanks, 
tb

---

### Post by XDevHald on 2009-09-03
I would recommend staying off of Jaunty for now as it's in alpha 5 and is not yet to release a full source without any real major bugs. The one thing I would say is that your kernel could be an issue with your xorg.conf file (graphics) and may not have the correct components to run it through.

Secondly the grub (boot load) may have been a sour download in which could have caused a (no image found) for your OS to run correctly or at all. If you can just run in between 8.04 and 9.04 without touching 9.10 just to be safe. If you're upgrading then please also becareful as some stages of firefox 3.5 or lower are causing a sever lack of image loading and network responde even if you tweak the about:config.

Third issue on upgrading is it may also cause drag+drop from files to folders and which could freeze your response time with Ubuntu. Grab the fresh CD's for free at [http://www.ubuntu.com](http://www.ubuntu.com) this way you have fresh installations and no upgrade hassels unless told otherwise by a dev.

If you can next time you get an issue such as this one (if you're able to load the desktop) search your /var/log/message and provide us the input of the log.

---

### Post by jrox717 on 2009-09-04
>  I would recommend staying off of Jaunty for now as it's in alpha 5 and is not yet to release a full source without any real major bugs. 

It's Karmic that's in alpha 5... Jaunty is stable and has been since April.

Sorry tb56, but the online upgrades have had a history of problems and without more info it's going to be hard to diagnose. I would recommend installing with a separate /home partition this time so that when you upgrade the next time (through a fresh install) you can keep all your personal documents and settings.

---

### Post by XDevHald on 2009-09-04
> **jrox717 said:**
> It's Karmic that's in alpha 5... Jaunty is stable and has been since April.

Sorry tb56, but the online upgrades have had a history of problems and without more info it's going to be hard to diagnose. I would recommend installing with a separate /home partition this time so that when you upgrade the next time (through a fresh install) you can keep all your personal documents and settings.

My apologies as I was not clear on this. Jaunty is stable but Karmic is not stable as of yet. Thanks for the clear up jrox and the support for the /home partition run upgrading (this is what I am doing right now with Jaunty 9.04).

Best of luck!

---

