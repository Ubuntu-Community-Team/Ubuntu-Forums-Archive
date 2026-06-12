---
title: "Installing 13.04 on Chromebook"
date: 2013-05-09
forum: Hardware
---

### Post by Roasted on 2013-05-09
A few days ago I got curious enough to give 13.04 a shot on the Samsung Chromebook. I ran into an array of problems, mostly with installing it. First, each guide I found was wildly different to the next. Some were just dual booting to the SD Card/SSD, others were installing to the internal SSD. I successfully got Ubuntu 12.04 on it but I had hoped to give 13.04 a shot. I rebooted a few times and to my surprise ChromeOS came back with no sign of Ubuntu.

I know it's probably a long shot and/or insanely infatuated headache to accomplish this, but for the sake of curiosity and why not I figured I'd look deeper. Instead of shuffling through countless guides that were posted when 13.04 was in alpha or whatever, I got to wondering if anybody here has succeeded with this. Can anybody comment, or link to a guide that worked for them? I wouldn't mind nuking ChromeOS and giving 13.04 the entirety of the internal SSD. Any insight would be appreciated!

---

### Post by oldrocker99 on 2013-05-12
Well, I have an Acer C7 running Chrubuntu 12.04. I tried upgrading to 12.10, which worked. I then tried upgrading to 13.04, and it hung in the middle of upgrading, for hours. I had to start from fresh, reinstalling ChromeOS, then reinstalling Chrubuntu. All is well now, and it's not like 12.04 is, well, BAD or anything. 13.10, with kernel 3.9+, may directly support my Chromebook.

Bear in mind that Acer is offering an upgraded version of the C7, with a 5000 mAh battery (mine has a 2500 mAh), and 8 GB of RAM (mine has 2 GB, and, oh yes, I'm upgrading). The price is said to be aboru $280, which is probably worth the extra $80. Even with 2GB ram, Chrubuntu 12.04 is pretty damn snappy, allowing me to use pan and GIMP, and play a surprisingly large number of games, including the Half-Life series, Portal, Bastion, Warzone 2100, etc.

---

### Post by aysiu on 2013-05-12
I just did this yesterday on my Chromebook. At first I tried the dual-boot with SD card, but that was a bit annoying, because (as you probably already know) most SD cards jut out of the Chromebook when inserted all the way, and for a dual-boot you have to, of course, reboot in order to switch OSes.

After fiddling around with that option, I ended up installing Xubuntu using Crouton, and it's amazing! This is the guide I used:
[http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/](http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/)

Didn't have much success upgrading Unity Precise to Unity Quantal or Raring, so if you want Raring (as I did), I'd recommend just install Xfce Raring straight away: ```
sudo sh -e ~/Downloads/crouton -t xfce -r raring
``` The big bonus of Crouton is that you can switch back and forth between ChromeOS and Ubuntu just with key strokes. I'm not sure on the mechanics of it, exactly, but it uses *chroot* to run both at the same time. It's not virtualization, and it's not a dual-boot, so you don't get any performance hit, and you don't have to reboot to switch.

I hope that helps.

---

