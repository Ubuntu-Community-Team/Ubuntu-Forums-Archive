---
title: "Whole system became slow and constantly freezes audacious/nautilus/firefox etc."
date: 2008-08-18
forum: General Help
---

### Post by kramer65 on 2008-08-18
Hello,

I had ubuntu installed on my previous computer which had become a relative oldie (pentium 4, 3gh, 1gb memory). I bought a new computer (quadcore 2.66gh, 4gb memory) on which I did a fresh 8.04 install. I installed many other things; Nvidia beta driver (173.14.12) using EnvyNG, audacious, flash for firefox, mp3 support, virtualbox etc. etc.

Things worked perfectly in the beginning. But slowly the system is getting less and less stable. First Audacious started giving me trouble. Not playing a song, random freezes etc. A restart used to fix the problem in the beginning. Then flash stopped playing videos after two seconds, sound doesn't work anymore. Sometimes a cleanup of the cache works, other times it doesn't and the problem seems to worsen. Many divx movies don't play correctly anymore using vlc or any other player (sometimes no sound, sometimes scrambled screen), and recently nautilus started to freeze when opening large folders (with which I had no problems in the beginning), gnome menu's (sometimes) open with a very very long delay (up to a minute), and even the system monitor started to freeze or go slower than normal.

I have no clue what the problem is since there is no specific application that has a problem, and problems start to spread across the whole system.

Can anybody help me out here? Do I need to do a reinstall of the whole system? That would be a big hassle though..

---

### Post by gjoellee on 2008-08-18
well, you should check the processes running...very often for WINE users wineserver is using 100% CPU, the same with firefox in some cases...go to System->Administration->System Monitor, check the processes and look for something that use MUCH CPU, if you don't need it running kill it! This may happen if you are running FLASH or JAVA, if so changing to Linux Mint may be the best solution

Also if you might have a look at some tweaks I have added to my home page:
[http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed?cr=2](http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed?cr=2)

---

### Post by kramer65 on 2008-08-18
Well, currently, I've got no problem. I could try to open about 15 firefox tabs with youtube, a movie, and some more stuff to see what happens..

But I've checked the system monitor while having an audacious freeze for example as well. Nothing major and the charts gave nothing major either (all cores below 25%). Also, I think it is quite a heavy computer which I bought. That should be able t run ubuntu pretty well I thought right..?

ps. As I think of it,there's another little thing. While booting up I don't see the bootloader anymore but just text saying "Loading.... OK". Maybe not very important, but still... why?

---

### Post by ZeldaFan on 2008-08-18
If audacious, flash videos, and sound is giving you a problem, you could be experiencing some problems with the PulseAudio sound server. You might want to use Alsa instead. Your computer most definitely can handle Ubuntu by the way; I wouldn't worry about your specs being too low. I am using your Nvidia driver, so I highly doubt that that is causing any problems.

---

### Post by kramer65 on 2008-08-18
OK. the sound server might give me trouble.. How do I install alsa?

---

