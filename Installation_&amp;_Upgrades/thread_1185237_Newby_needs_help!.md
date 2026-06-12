---
title: "Newby needs help!"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by fredcrn on 2009-06-12
Have been running 8.04 for a while. Set it up with windows xt. Ubuntu is loaded on a separate hard-drive. Tried to upgrade to 9.04 yesterday and when the process was finished, system boots to tan screen with cursor and stalls. No desk top. Noticed the start up screen still lists 8.04 not 9.04. Is there an easy fix for this? I'm pretty much retarded when it comes to ubuntu. If not, can I format the hd and reinstall 8.04?
Thanks
Fred

---

### Post by woozly on 2009-06-12
boot system in runlevel 1.....
[http://ubuntuforums.org/showthread.php?t=1172992](http://ubuntuforums.org/showthread.php?t=1172992)
 
after that reconfigure X. 
 
goto command line and run **sudo dpkg-reconfigure xserver-xorg** then restart X
 
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
[http://ubuntuforums.org/showthread.php?t=1135585](http://ubuntuforums.org/showthread.php?t=1135585)
 
chears 
woo

---

### Post by Bucky Ball on 2009-06-12
One question: why did you decide to upgrade if you had a stable system?

If there is no entry for 9.04 in the grub menu and you can only boot into 8.04, isn't that what you want to do? You could reinstall whatever version you like, go for manual partitioning and wipe the drive before you set up your partitions.

---

### Post by fredcrn on 2009-06-12
> **Bucky Ball said:**
> One question: why did you decide to upgrade if you had a stable system?

If there is no entry for 9.04 in the grub menu and you can only boot into 8.04, isn't that what you want to do? You could reinstall whatever version you like, go for manual partitioning and wipe the drive before you set up your partitions.

Did I mention I'm Ubuntu retarded? I was thinking if 8.04 was good then 9.04 would be improved. Isn't that how it's supposed to work? I no longer can boot to 8.04 and it won't boot to 9.04 either. Just a blank tan colored screen. Guess I'll try reinstalling 8.04, as the previous post is beyond my limited capabilities.
Fred

---

### Post by Bucky Ball on 2009-06-12
K, I follow. It works like this. 8.04 LTS (long term support) has been around since April '08 (4th month of 08 backwards) and is supported until April 2011 (from memory). Because it has been around for over a year, it is pretty stable. It is a matter of if it ain't broke, don't fix it. Having said that, to improve and progress, users test versions and help to iron out bugs in newer versions. Feel free to do that and file any bug reports once you have used 8.04 for awhile and get the feel of how Ubuntu works. The community needs testing users. In fact, you could file a bug report about the problem you're having now, or look for one already filed.

Something people do, and I intend to do the same once I can fix my damn desktop (it dies for the first time ever as I start 6 weeks holidays!), is to have a solid, workhorse version (8.04 say) on one partition, and a testing version (Karmic Koala, I can't wait to have a look) on another partition, which you don't need to rely on (because you have your stable install to fall back on). You've then also got a tool for learning more about how the system works without worrying about breaking the system. If you break the install so badly, you can just reinstall onto your 'testing' partition again.

As for now, as a newbie, the most problem free and stable would be 8.04 LTS. If you start to feel comfortable using in a terminal, then dip into the newer versions. If not, stick with the LTS versions. Believe me, tweaking Ubuntu to fix things gets easier as you go. If you have come from a life of Windows, it is different and just takes a bit of getting used to.

Too much information! Have fun ... :)

* Edit: Check out the pocket guide at this link. Under "Installing Ubuntu," there is a much better explanation ...

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

### Post by fredcrn on 2009-06-12
> **Bucky Ball said:**
> K, I follow. It works like this. 8.04 LTS (long term support) has been around since April '08 (4th month of 08 backwards) and is supported until April 2011 (from memory). Because it has been around for over a year, it is pretty stable. It is a matter of if it ain't broke, don't fix it. Having said that, to improve and progress, users test versions and help to iron out bugs in newer versions. Feel free to do that and file any bug reports once you have used 8.04 for awhile and get the feel of how Ubuntu works. The community needs testing users. In fact, you could file a bug report about the problem you're having now, or look for one already filed.

Something people do, and I intend to do the same once I can fix my damn desktop (it dies for the first time ever as I start 6 weeks holidays!), is to have a solid, workhorse version (8.04 say) on one partition, and a testing version (Karmic Koala, I can't wait to have a look) on another partition, which you don't need to rely on (because you have your stable install to fall back on). You've then also got a tool for learning more about how the system works without worrying about breaking the system. If you break the install so badly, you can just reinstall onto your 'testing' partition again.

As for now, as a newbie, the most problem free and stable would be 8.04 LTS. If you start to feel comfortable using in a terminal, then dip into the newer versions. If not, stick with the LTS versions. Believe me, tweaking Ubuntu to fix things gets easier as you go. If you have come from a life of Windows, it is different and just takes a bit of getting used to.

Too much information! Have fun ... :)

* Edit: Check out the pocket guide at this link. Under "Installing Ubuntu," there is a much better explanation ...

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

Thanks for the reply. I guess at this point I'll just format the hd and try installing from the beginning. A little upset I'll loose my bookmarks and stuff, but thus is the price of ignorance. Getting to old for this crap, but really hate windows. Maybe I'll just go buy an apple.
F

---

### Post by merlinus on 2009-06-12
If you had a separate /home partition, then your bookmarks, filled-in form information, and application settings and configurations would not be lost.  You simply choose to not format that partition when upgrading or reinstalling.

So you may wish to consider this option when doing your reinstall.

---

### Post by Bucky Ball on 2009-06-12
> **merlinus said:**
> If you had a separate /home partition, then your bookmarks, filled-in form information, and application settings and configurations would not be lost.  You simply choose to not format that partition when upgrading or reinstalling.

So you may wish to consider this option when doing your reinstall.

Indeed. Sounds like you had 8.04 working. Just reinstall and this time make a partition big enough for the operating system and *not* your personal data, and partitions for everything else. Most apps can be set to open a specific location or store things in a specific location (like Firefox, Thunderbird and heaps of others) other than /home or /thunderbird/?.

:)

---

