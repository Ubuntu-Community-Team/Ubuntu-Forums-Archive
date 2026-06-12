---
title: "HELP please! - can't install nvidia driver"
date: 2009-11-23
forum: Hardware
---

### Post by tjk on 2009-11-23
I've been using Ubuntu for several years now.  I did have problems installing the NVidia driver in the early versions of Ubuntu, but nothing since. However, this upgraded to Karmic 9.10 (64-bit) has given me nothing but continual problems (esp with this NVidia driver)!!!  I've been working at this for weeks now and I probably would have saved a lot of time doing a complete reinstall of Ubuntu... but maybe I'll learn something if I can figure this problem out!

Here's a few things that are odd when booting my computer. 
1)  I upgraded to Grub2 at the same time as upgrading to 9.10 and the converted menu created a list of seemingly duplicate kernel startups. Don't know if this has anything to do with my video problem as:
2)  I can boot to the nv driver with no problems (but I need the nvidia driver as it is much faster and has other features that I need.)
3)  When starting the Driver "nvidia" in xorg.conf I get the "low graphics mode menu box.  If I select start one instance, the low graphics mode menu box pops up again.  If I select the "start one instance" again I'm dropped to the command prompt (although it flashes several times as if trying to start something again).  If I select to drop to command prompt a warning box pops up and states that the following sessions are running: TTY login -- vt1 and, TTY login -- vt2 (don't know what this means).


PLEASE give me your ideas on how I might fix this annoying problem, and I can tell you if it works or not.

---

### Post by fancypiper on 2009-11-23
Have you tried installing the driver by clicking System>Administration>Hardware Drivers?

---

### Post by tjk on 2009-11-23
> **fancypiper said:**
> Have you tried installing the driver by clicking System>Administration>Hardware Drivers?
Thanks for responding...

I did try this... it shows that the driver is installed.  I don't know how it can say this since the xorg.conf file doesn't even contain the word NVidia (it is using the nv driver).

---

### Post by tjk on 2009-11-24
I still can't get the driver installed... any other ideas?
> **tjk said:**
> 
I did try this... it shows that the driver is installed.  I don't know how it can say this since the xorg.conf file doesn't even contain the word NVidia (it is using the nv driver).

---

### Post by fancypiper on 2009-11-24
Did you reboot after installing the driver?

---

### Post by tjk on 2009-11-28
> **fancypiper said:**
> Did you reboot after installing the driver?

Yes, I have rebooted.

---

### Post by tjk on 2009-11-28
Here's a few other things that I've tried:

I removed kdm, then rebooted... thinking I would be sent to the prompt after rebooting.  Instead a debian desktop manager appears.  I then removed wdm and rebooted.  After this I was sent to the prompt. I then reinstalled the gdm (which was the manager that I had used before updating to 9.10).  At this point I no longer had the "low graphics" screen appear two times -- so that problem was solved.  Still couldn't get NVidia driver installed.

I've tried reinstalling envyng-core and then running envyng --uninstall-all. (I had tried previously using envyng to install nvidia, with no success.)  Then I purged envyng-core.  I then purged NVIDIA*, so that I would have no trace of the nvidia driver.  Then I reboot in recovery mode.  Changed to init 3. Changed to the folder where I had downloaded the most recent NVidia bash script.  Then I ran the script -- everything appeared to have completed correctly -- the script ended with it telling me that it had been installed.  Then I rebooted, and was once again given the "low graphics" notice.  (I even tried running in low graphics, logging on to KDE and then rebooting -- but I was just sent to the "low graphics" screen again.

I then tried to install an earlier kernel (2.6.31-14).  I went through the whole process above, but the result was exactly the same.

I have tried other things before the above listed items... I will post them as I try them... but in the meantime I would welcome any advice or ideas that people have...

---

### Post by tjk on 2009-12-06
I'm beginning to wonder if my graphics card is supported in 9.10.  Other people are having problems with the NVidia GeForce4 AGP video card.  

Anyone have this card working in karmic?

(I've messed around so much that I can't even run the nv driver... I'm running with vesa now.)

I've also been reading that some can install GeForce drivers in 2.6.31-14 but not 2.6.31-15  -- I can't get either to work.

---

### Post by ratcheer on 2009-12-06
Here are the standard instructions for installing the nVidia drivers. They have always worked for me. If this is what you are already doing, then I don't know.

1) Get to a console terminal by entering Ctrl-Alt-F1
2) Terminate the GDM: sudo /etc/init.d/gdm stop
3) cd to the directory where the nVidia driver run file is stored.
4) sudo sh ./xxxxxxxxxxxxx.run
5) When the install script asks if you want to auto config the xorg.conf, reply Yes
6) sudo reboot

I hope this helps.

Tim

---

### Post by jocko on 2009-12-06
> **tjk said:**
> Thanks for responding...

I did try this... it shows that the driver is installed.  I don't know how it can say this since the xorg.conf file doesn't even contain the word NVidia (it is using the nv driver).
Try to rename your existing xorg.conf and make a new one using nvidia-xconfig:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-xconfig
```



If things gets horribly messed up after this (not very likely), you can get back to your current semi-functional setup by booting into recovery mode and running this, then reboot:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by smilingralph on 2009-12-06
Are you trying to install the right driver? I believe that card requires a legacy driver like the one [here]("http://www.nvidia.com/object/linux_display_amd64_96.43.14.html"). [This]("http://ubuntuforums.org/showthread.php?t=1125400") is an excellent tutorial on installing Nvidia drivers. Good Luck
Ralph

---

### Post by tjk on 2009-12-07
I did try this about a dozen times... thank though...

> **ratcheer said:**
> Here are the standard instructions for installing the nVidia drivers. They have always worked for me. If this is what you are already doing, then I don't know.

1) Get to a console terminal by entering Ctrl-Alt-F1
2) Terminate the GDM: sudo /etc/init.d/gdm stop
3) cd to the directory where the nVidia driver run file is stored.
4) sudo sh ./xxxxxxxxxxxxx.run
5) When the install script asks if you want to auto config the xorg.conf, reply Yes
6) sudo reboot

I hope this helps.

Tim

---

### Post by tjk on 2009-12-07
I did this several times too...

> **jocko said:**
> Try to rename your existing xorg.conf and make a new one using nvidia-xconfig:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-xconfig
```

If things gets horribly messed up after this (not very likely), you can get back to your current semi-functional setup by booting into recovery mode and running this, then reboot:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by tjk on 2009-12-07
In all my attempts to install the NVidia driver I did get them from the NVidia site, as you specified below.  I didn't use the tutorial below to get the problem solved, but I did bookmark the location for next time...

> **smilingralph said:**
> Are you trying to install the right driver? I believe that card requires a legacy driver like the one [here]("http://www.nvidia.com/object/linux_display_amd64_96.43.14.html"). [This]("http://ubuntuforums.org/showthread.php?t=1125400") is an excellent tutorial on installing Nvidia drivers. Good Luck
Ralph

---

### Post by tjk on 2009-12-07
Okay, I FINALLY got the NVidia driver working!!!  At this point I can't tell exactly what I did to solve the problem because I did a number of things at once.  It could have been the new kernel that I installed (now running 2.6.31-16) or it could have been one of the many daemons that I disabled with "Bootup-Manager" -- it seems to me that a long time ago I had problem with TIMIDITY conflicting with the NVidia driver.  If anyone knows of a list of apps that conflict with NVidia - please let me know.

Anyway... thanks to all you who attempted to help me with this problem... it would be a HUGE improvement if Linux could deal with this display driver issue once and for all!

---

### Post by QuanTime on 2009-12-07
bit late on this.. bit i had NVidia driver issues for a bit, did the hardware drivers update thing, version 185 (it was on 173 and there were throwing bulk errors).  That fixed it right up.

Glad to hear you got it sorted.

---

