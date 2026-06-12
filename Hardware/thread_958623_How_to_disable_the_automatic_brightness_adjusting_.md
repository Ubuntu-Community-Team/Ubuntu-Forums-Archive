---
title: "How to disable the automatic brightness adjusting feature?"
date: 2008-10-25
forum: Hardware
---

### Post by lores on 2008-10-25
Hello!

I've got an issue with a HP 6720s laptop. It concerns the automatic brightness adjusting feature of Ubuntu (8.04 u-t-date), very similar to the bug described here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg915816.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg915816.html).

So, I'd like to use my laptop's screen at the lowest brightness level nearly all the time, whereas Ubuntu seemingly tries to adjust it for me, setting it to the very highest lvl on every occasion, eg. after 40 secs of inactivity (power_managment_delay), screen lock, screen blanking (yes! the screen ought to be blanked, and yet it gets black AND max-bright!; is that power saving?), vbox machine run, film playing, resuming from anything (sus-to-ram, s-t-disk), opening the lid.

This is VERY annoying and battery-unfriendly, and I have no clue how to disable it, although I've been struggling with this issue for a few weeks now...

I am ready to resign from all auto adjusting features, as I would preferably run the screen at lowest br. lvl as default (almost all the time), but with the ability to temporarily reset the brightness manually with hotkeys (fn+f7/8 keys work) - would be great if these re-set br. values were kept constant as well...

From the cited bug report I assume it is somehow possible by blacklisting a video driver - which one, where? Is there really no other way? Blacklisting a driver is probably going to lead to different troubles (performance, power)...

I am really quite desperate, as this feature appears to effectively disturb any work I intend to do with the notebook. I've dug through all settings I could find, certainly utilising Google as well. I've experimented with the GUI of gnome-power-management and I visited gconf also (especially sections gpm and g-screensaver)...

Thx!

---

### Post by lores on 2008-10-27
Anyone?

---

### Post by lores on 2008-10-29
Come on...

---

### Post by eentonig on 2008-10-29
Not very usefull, but just so you get a reply. 

No idea.

---

### Post by lores on 2008-10-29
Thanks a lot for this positive flavour :) .

*

Hey, guys! It's the big day of 8.10 today, so why won't you just quickly type a simple solution here? :D

---

### Post by DanTheFlyingMan on 2008-10-30
My laptop was setting itself to 0% brightness when certain programs opened. I fixed it by going to the terminal and typing:

```
sudo gedit /etc/modprobe.d/blacklist
```

I then added:

```
# horrible brightness adjustment thing
blacklist video
```

to the end of the file. Hopefully it will work for you too.

---

### Post by lores on 2008-10-30
Thank you very much for the support. I'm going to try out that method, yet are there any side-effects? Well, it's blacklisting the video driver after all, isn't it?

---

### Post by DanTheFlyingMan on 2008-10-30
> **lores said:**
> Thank U very much for the support. I'm going to try out that method, yet are there any side-effects? Well, it's blacklisting the video driver after all, isn't it?

I haven't seen any side-effects or loss in graphical performance at all. It isn't hard to undo if something does go wrong though.

---

### Post by lores on 2008-10-31
OK, thanks a lot! After I've dealt with 8.10, I'll try that!

EDIT: I've found another work-around - if I set the default brightness-level (in the power-settings) to the second lowest value, it works like a charm and does not get changed by anything anymore!

---

### Post by daqron on 2011-02-15
> **DanTheFlyingMan said:**
> 
```
sudo gedit /etc/modprobe.d/blacklist
```

I then added:

```
# horrible brightness adjustment thing
blacklist video
```

to the end of the file. Hopefully it will work for you too.

Yay! I have had a similar issue on my **HP EliteBook 6930p** (notorious for a myriad of brightness control issues in Ubuntu). My specific issue was that despite having all software brightness control turned off, it would still dim the screen whenever the power mode switched (either switch to or from battery power). I kept having to manually reset the brightness where I wanted it every time I changed power sources.

Anyway, this totally worked. I had to create the file, but after doing so and making the noted change, and a reboot, it worked.

Cheers for the solution!

---

### Post by another_sam on 2011-12-06
> **daqron said:**
> Yay! I have had a similar issue on my **HP EliteBook 6930p** (notorious for a myriad of brightness control issues in Ubuntu). My specific issue was that despite having all software brightness control turned off, it would still dim the screen whenever the power mode switched (either switch to or from battery power). I kept having to manually reset the brightness where I wanted it every time I changed power sources.

Anyway, this totally worked. I had to create the file, but after doing so and making the noted change, and a reboot, it worked.

Cheers for the solution!

This does not work on Asus U36JC + Ubuntu 11.10.

edit: but [http://askubuntu.com/questions/18603/how-to-stop-gnome-power-manager-from-changing-the-global-backlight-setting](http://askubuntu.com/questions/18603/how-to-stop-gnome-power-manager-from-changing-the-global-backlight-setting) does.

---

