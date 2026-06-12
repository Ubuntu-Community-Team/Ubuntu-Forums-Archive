---
title: "Sound Problem in Ubuntu 7.04"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by funalien on 2007-07-13
I have been working on Ubuntu Feisty Fawn for about 2-3 months, and one day all sounds dissaperred. I have Realtek AC97 sound card intergrated in motherboard nVidia. I'am newbie in using Linux, so I want to get help and any suggestions. :)
One interesting thing is that my sound works in ubuntu after starting windows. => 
Then I start ubuntu, where is no sound. After that I load Windows, there is no sound too. But after doing this I can load Ubuntu or Windows again, and then sound works perfectly.  
:(

---

### Post by acaby on 2007-07-18
I am not sure this solution will correct your problem but it certainly will not hurt to try.
Go to topic:[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and especially pay attention to the area that I have pasted below:

Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot
[*][left]
VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm xubuntu-desktop


(3) Reboot

Hope this helps,
Arthur
p.s. I am using ubuntu 7.04 and my sound was working perfectly until I updated about 180mb. Then the sound would not work. I applied the aforementioned solution and now it works perfect. (Must have been a bug in one of the upgrade files)

---

