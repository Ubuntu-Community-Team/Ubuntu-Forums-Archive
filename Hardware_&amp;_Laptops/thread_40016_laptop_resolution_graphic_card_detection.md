---
title: "laptop resolution/ graphic card detection"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by byen on 2005-06-07
ok... I know this question has been posted many times but I looked around and found nothing much.....
After I installed ubuntu...everything went well...it detected my hardware and said I have a radeon mobility graphic card and the screen was ok! the highest resolution i could get was 1028X768 and 60Hz and I thought (duh!) that this was the best it could give out. And now i see at various posts that this is really not the best my card can offer!! infact ive seen screen shots with very impressive resolutions... I have an lcd laptop monitor and my screen looks like an Win95 screen... is there anyway to fix this... please suggest.

By the way I have an ATI-radeon 7500 graphic card (64mb) and an lcd flat panel (laptop) monitor.

thank you guys.

---

### Post by Zodiac on 2005-06-07
I have that same problem.

I would also love an answer... thanx!

---

### Post by byen on 2005-06-07
[QUOTE=Zodiac]I have that same problem.

I would also love an answer... thanx![/QUOTE]
 wow...nobody? either the guys are tired of answering this Question or I posted this in the wrong thread. anyone..?

---

### Post by mfairchilds on 2005-06-07
Your graphics chipset is capable of much higher resolutions, but your LCD probably  maxes at 1024x768.  That's the limit on my Thinkpad.  Try an external monitor just to check if you have one.  Best of luck.

---

### Post by byen on 2005-06-07
Im sure about my monitor running higher resolutions as I have been able to do it on XP and also... Ive seen someone run Fedora with higher resolutions on the same make/model.

thank you for the input though.

---

### Post by holomorph on 2005-06-07
did you try:
sudo dpkg-reconfigure xserver-xorg
and choosing a higher resolution as the max?

---

### Post by byen on 2005-06-07
yup- no good! thanks though.

---

### Post by tread on 2005-06-08
Try to grab the modelines from xorg.conf/xfree86config from the fedora installation .. alternately, try generating one at [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) 

Over [here](http://www.d.umn.edu/~salu0005/linux_installation.html) I have briefly mentioned how to use the modelines  to get your desired resolution up.

---

### Post by myer0052 on 2005-06-08
Check out this thread on setting up the ATI Radeon Drivers, it should work for your model as well. Plus then you will get 3d acceleration:


[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

---

### Post by byen on 2005-06-08
[QUOTE=myer0052]Check out this thread on setting up the ATI Radeon Drivers, it should work for your model as well. Plus then you will get 3d acceleration:


[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)[/QUOTE]
 I checked the thread out..though it is a great work-around mine is a ATI radeon 320M which uses the 7500 chipset and the thread says:
And from the website linked to above:
Quote:
# MOBILITY™ RADEON™ 9000, 9200, 9600, 9800, X700
# MOBILITY™ RADEON™ 9000/9100 IGP Series
are supported

They support the X700, 9800, 9600, 9200, and 9000 Mobile chipsets.

Hence mine is OUT! i really appretiate the help guys..but my screen is so bad that when I move my window it breaks up and moves in frames..bit by bit...! Oh brother!

---

### Post by jrhodes on 2005-06-08
bring up a terminal and type lsmod |grep radeon.

hotplug *should* be loading the radeon DRM module on boot, but if it doesn't, then X will default to non-accelerated graphics. 

If radeon isn't loaded, then stick it in /etc/modules and reboot. That should take care of it.

---

