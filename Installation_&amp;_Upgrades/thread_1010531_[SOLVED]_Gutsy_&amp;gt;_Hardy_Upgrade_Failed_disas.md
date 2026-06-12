---
title: "[SOLVED] Gutsy &amp;gt; Hardy Upgrade Failed disastrously"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by Berethorn on 2008-12-13
Been running Gutsy for about a year now and today I decided to finally upgrade from 7.10 to 8.04 (and possibly to 8.10 afterwards).

I upgraded via the Update Manager. Took about three hours to download, then it started the install process. I was doing something else at the time, checking in every few minutes to choose either to keep or replace certain files that had been edited. Near the end it said there was a problem installing mythtv - I wasn't worried, I don't need mythtv - then another file couldn't install (I'm sorry, I don't remember which, I didn't think much of it at the time) and I chose to submit the debug info to Ubuntu dev. Then it continued to install. It was almost finished. Again it told me mythtv couldn't be installed. I have no idea if that's important. But then just as I thought it was done it gave me an error, saying something to the effect of "the update manager couldn't complete the upgrade." and that it would run dpkg to revert the install. It said the computer may be in an inoperable state. It closed.

I wasn't sure if the upgrade had failed completely or not, so I checked the computer info and it said "Ubuntu 8.04" was installed. I opened Swiftweasel to see if the internet worked - it did, but SW was slow. Nothing else seemed different, but I thought a restart would clear things up. I restarted, went away a couple minutes, and came back to see that it hadn't got past the orange/pink startup screen, with only the cursor in the center, everything completely frozen. And that's where I stand after restarting it again. I have no idea what to do. :( Please help! Luckily I have a separate /home directory, but I was hoping upgrading this way would be smooth.

---

### Post by falcon61102 on 2008-12-13
It may be that you simply need to configure your graphics chip.  What type of graphics card/chip are you using?

If you did want to reinstall, the quickest and easiest method to get back up and running at this point would be to download and install a fresh install, especially since you have a seperate /home partition.

That being said, if you want to try to rescue this install, try booting up with an old kernal version or with the current recovery version from the GRUB.  That may be able to get you around the graphics issue so you can finish the install.

---

### Post by Berethorn on 2008-12-13
Thanks, I booted up the recovery mode and got into gnome - what a relief!

Hardy SEEMS to be installed. But I don't know how to tell if the upgrade is complete or not. The Update Manager can't find anything new to update - either that's good and everything is installed, or bad and it isn't working.

My emerald theme is disabled - compiz has taken over, but the whole desktop environment feels slower (and playing a video fullscreen in totem was terribly slow). That's unacceptable but fixable, I hope. I have an ATI card. The restricted drivers manager popped up for the ATI driver so I enabled it and restarted, but I couldn't get into my desktop after. Will have to survive on the default driver for a bit. But I have a nice new nVidia card waiting to be installed - maybe now's a good time to stick it in.

For now, how do I determine the status of the upgrade? If I had a choice I would rather save this installation. :\

---

### Post by Berethorn on 2008-12-13
Actually, now I can't get into Gnome.

"The Gnome session manager was unable to lock the file /home/username/.ICEauthority"


EDIT: found a fix on another thread:

> Ctrl+Alt+F1 to a console and log in and then:

chown yourusernamehere ~/.ICEauthority
sudo chmod 777 /home/yourusernamehere/.ICEauthority
sudo /etc/init.d/gdm restart

---

### Post by Partyboi2 on 2008-12-13
Open a terminal (Applications>Accessories>Terminal) and see if you get any output to
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```

Have you tried disabling desktop effects (System>Pref>Appearance>Visual Effects) to see if things speed up?

---

### Post by Berethorn on 2008-12-14
Followed your commands, and the only two errors to pop up are with mythtv-database and mythtv. Those refuse to install, but there's no mention of anything else. I have a feeling the upgrade was actually successful, in a buggy way.

Oddly enough the graphics behave worse when the visual effects are turned to None or Extra. Normal works best, but not well. I will try a newer version of fglrx, perhaps. :)

I'm wondering if I should go straight to 8.10 from here (before spending time configuring 8.04), or if I should learn my lesson and stop meddling now.

---

### Post by utnubuuser on 2008-12-14
This may seem rude, but why do people upgrade instead of doing a new install, when it's been well documented that upgrading doesn't work for squat?
Isn't it just as easy to use gparted, slide the old install aside, do a fresh install, importing all docs and settings, then removing the old version once the new one is up and running?

---

### Post by Berethorn on 2008-12-14
I know not. In fact that method is new to me. I should have done more research. But upgrading internally was recommended on Ubuntu's website.

Do you happen to know of a place with instructions for the method you mentioned? I'd be much obliged; I can't find anything on this forum. :)

---

### Post by falcon61102 on 2008-12-14
You may be better off going straight to 8.10 at this point before configuring too much as you'll have to reconfigure most things once you get there.

As far as your graphics acting sluggish, that is likely cause by incorrect or non-existant drivers.  But again, if you're planning on going to 8.10, I wouldn't waste too much time tinkering with 8.04.

---

### Post by Berethorn on 2008-12-14
Well, thanks for the help! I've decided to stick with 8.04 LTS for now.

I installed my new nVidia 8800GS graphics card, which worked out of the box, but took two hours to get compiz working on (finally did it through envyng).

Spent the rest of the day playing around, configuring, having fun. It all worked out in the end. :)

---

### Post by falcon61102 on 2008-12-15
Glad you got everything worked out for now.

---

