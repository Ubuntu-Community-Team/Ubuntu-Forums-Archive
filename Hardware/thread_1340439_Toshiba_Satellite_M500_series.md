---
title: "Toshiba Satellite M500 series"
date: 2009-11-28
forum: Hardware
---

### Post by wafflemelon on 2009-11-28
A thread for owners of Toshiba Satellite M500 & M505 laptops to post their experience of setting up Ubuntu.

I've had no trouble installing Ubuntu and gfx drivers for the ATI Radeon card.

However, I and many others have problems with getting the fan to work, leading to an overheating problem.

Here are accounts of other users:
[http://ubuntuforums.org/showthread.php?t=1282161](http://ubuntuforums.org/showthread.php?t=1282161)
[http://ubuntuforums.org/showthread.php?t=1326744](http://ubuntuforums.org/showthread.php?t=1326744)

Anyone with solutions, reply here! I'll be sure to update this post as solutions are found.

---

### Post by derekmbarnes on 2009-12-31
This thread is badly needed for us Satellite users (and could possibly be helpful to others as well), so I'll just post every problem I've seen so far...

_Fan control:_ *Fan works at limited capacity/does not work at all*
May have something to do with ACPI/BIOS "trip point" settings; no fix as of yet. In the meantime, this user recommends using an external cooling system if available.

_Wireless:_ *Wi-Fi won't connect*
**Solved.** This model should be equipped with a Realtek 8172 network controller (use code "lspci" to confirm this). Linux-native driver for this model and instructions for installation are found here: [http://forum.novatech.co.uk/showthread.php?p=197789](http://forum.novatech.co.uk/showthread.php?p=197789)

_Controls:_ *"Media control" strip locks up the system*
From what I can tell, these "touch-and-go" buttons don't send an off-signal, acting as if they are continuously on. As a result, the system locks into the button's function (mute, volume, etc.), locking the user out of the entire system. Solution is a work in progress; meanwhile switching desktop screens via "Ctrl-Alt- ->" or "Ctrl-Alt- <-" is rumored to release the system.

_Controls:_ *Certain F-keys do not function*
**Solved. **This issue seemed to resolve itself; probably just a hiccup. *(3 Jan 2010)*

_Eco Mode:_ *Eco Mode utility is missing*
The Eco utility program is available from Toshiba in their "Downloads and Drivers" site: [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp?nav=Download](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp?nav=Download) . No word yet on whether it actually works; everything was made for Windows 7.

---

### Post by wafflemelon on 2010-01-01
Regarding the function keys, this seems like something that could work:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1718503.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1718503.html)

@derekmbarnes I'm away on a vacation, without Ubuntu. Could you confirm this?

---

### Post by philby.wak on 2010-01-12
I got Ubuntu 9.04 going with fan operating normally by using Sun VirtualBox on Windows7. Works well. Pity that it I need to run Windows first, but better than burning a new laptop.

---

### Post by wafflemelon on 2010-01-24
Unfortunately the processor I picked (for some inane reason) has no VT-x tag, thus won't virtualize squat. Thank you Intel

EDIT:
Virtualbox actually works! Why doesn't VMWare let me boot then? Is it just an artificial limitation?

---

### Post by m2xtreme on 2010-02-18
I found most of this info from another thread wafflemelon was following and figured I would add it here with the rest of what I found for the rest of you M500 users... thanks to all those who helped me get this far!

**To get the cooling fan to work without having to suspend and resume your computer do the following:**

Add "acpi.power_nocheck=1" to your boot options.  This will differ depending on what version of ubuntu you are using.  For versions prior to 9.10 the boot options can be found here

sudo gedit boot/grub/menu.lst (I believe... but I may be wrong!)

I'm using 9.10 so the boot options can be found here

sudo gedit /etc/default/grub

This change is because from the release of 9.10 on ubuntu will have GRUB2 as the default boot loader, its just the next version of GRUB.

Anyways you're gonna want to change the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi.power_nocheck=1"

Next, follow the instructions on this thread to install powersaved:
[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480) 

I didn't do any sort of configuration, I just installed and rebooted and everything worked fine for me.  This could be because I was messing around with powersaved earlier and uninstalled it because at the time I couldn't get it working, so if it doesn't work right away you should try following the tutorial on that thread further and do some configuration.

Lastly, I'd recommend installing lm-sensors and GNOME Sensors Applet to monitor your cpu and gpu temperatures just in case.

sudo apt-get install lm-sensors
sudo apt-get install sensors-applet  <-- you can use a different gui, this is just the first one I tried and it worked fine so I stuck with it.  For a more complete list check here:
[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)

After you've installed everything reboot and right click the panel and add "Hardware Sensors Monitor".  If all went well you should be able to run ubuntu and not worry about burning your laptop.  My laptop has been running around 45 C for hours now and I have restarted a few times so I'm pretty sure it's fixed :P

Hopefully this helps!

EDIT:  for Lucid I had to install liblazy1 and libpowersave11 manually from [http://packages.ubuntu.com/karmic/powersaved](http://packages.ubuntu.com/karmic/powersaved)

---

### Post by m2xtreme on 2010-02-22
I spent some more time messing around with my laptop today, particularly trying to see what I could do about getting the media keys and the brightness Fn keys to work.

It sounds like a lot of people with Nvidia GPUs are having trouble adjusting the brightness with the shortcuts, though using Nvidia X Server Settings to adjust the brightness work in the mean time for those who really need to.  That uses smartdimmer or nvclock or something.  It sounded like a fix could be implemented in the future, and I don't mess with brightness often enough to care so I'm giving up on that for now...

As for the media keys; volume up, volume down, mute, play, next track, and previous track buttons work for me, inconsistently at that. Usually they freeze up my menu in top panel or any program I'm using and I have to ctrl+alt+del and suspend/resume to get it working again. At least the volume doesn't get stuck like it used to when I used the volume media keys but it still doesn't work flawlessly for me, I'll keep posting.

In the mean time, if anyone can comment on what they have working it could help me in my searching.  Thanks :)

---

### Post by m2xtreme on 2010-02-22
**Sticky Media Buttons Fix**

This is an easy one, I'm somewhat disappointed I didn't think about it sooner.  Goto System>>Preferences>>Keyboard and under "Repeat Keys" slide the Delay slider to the right a little bit.  **You're Done!**

I'll leave it up to you to figure out how much is barely enough.  Also, I imagine you could just turn off repeat keys all together too, but then you wouldn't be able to easily spam the same keys over and over like a noooooooooooooooooooooooooob

enjoy:popcorn:

---

### Post by wafflemelon on 2010-03-27
m2xtreme , have you performed a stress test to see if temp returns to 45C?

If I left my laptop off for a few hours and turned it on, it would idle at about 45c. But if it was hot to begin with, it would idle at 55C.

Try playing nexuiz or running some other heavy-ish application for a few minutes! :)

---

### Post by m2xtreme on 2010-03-27
wafflemelon, I've had it shoot up to ~50 C while running a lot of processes but I also have been using an external laptop cooling fan to be safe, which could explain the slight difference in our maximum temperatures.

Sorry that this is a bit off topic but I wouldn't run Nexuiz nowadays.  I used to, but recently Nexuiz has now been sold to a new game development company called Illfonic, basically screwing over all the hard working contributors from the community.  I recommend you check out Xonotic ([http://www.xonotic.org/](http://www.xonotic.org/)).  Xonotic forked from the Nexuiz project to remain a free open source community game :D

Anyways, I'm not sure if ~50 C is too hot for this laptop.  Running windows 7 does stay a bit cooler but then again I don't really do anything stressful when I boot into windoze.  What do you think?

EDIT:
After really trying to push my laptop I got it to ~60 C... still better than before but not ideal at all.

---

### Post by wafflemelon on 2010-03-28
I see. I think 60C is too much. But if you idle after that, does it stay at 55C or 45C ?

---

### Post by m2xtreme on 2010-03-28
If I stop the strenuous activities it drops back to ~45 C

---

