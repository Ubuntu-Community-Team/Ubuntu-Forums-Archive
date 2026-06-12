---
title: "Help needed with soundcard noise (Intel/Realtek)"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by bogoliubov on 2007-08-08
Hello. I just bought a Clevo laptop (M540N) that came with Ubuntu preinstalled. Most stuff works nicely, but sometimes there is a high-pitched noise that is independent of the volume settings. 
The noice is not constant, and often disappears after having had the computer on for a few minutes. Often the sound comes back after waking the computer up from sleep.

I've read that there may be problems with this soundcard ( [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29) ) , but I don't know if my problem is the same as described on that page.

So, how can I find out if my soundcard suffers from a hardware fault, or if it's a problem with the driver??

Btw: anyone else out there who uses a Clevo laptop?

---

### Post by bogoliubov on 2007-08-08
Hmm, I've upgraded to the latest ALSA version, but no change. Any ideas of how I can set up Ubuntu so that the soundcard drivers aren't loaded at startup?

---

### Post by buntunub on 2007-08-08
Did you follow that entire guide all the way through to the very very end? What about this step - 

   >  *

      Edit the file /etc/modprobe.d/alsa-base

gksudo gedit /etc/modprobe.d/alsa-base

    *

      Add the following line to the file, replacing '3stack' with your model (see below for a complete list)

options snd-hda-intel model=3stack

    *

      Reboot

When you reboot, make sure that the power chord is NOT connected. That should fix things. If not, again without the power chord attached, hibernate and then recover, and then reboot again. That should do it.

---

### Post by bogoliubov on 2007-08-08
> **buntunub said:**
> Did you follow that entire guide all the way through to the very very end? What about this step - 

   

When you reboot, make sure that the power chord is NOT connected. That should fix things. If not, again without the power chord attached, hibernate and then recover, and then reboot again. That should do it.

Ok, well no I did not do the last step. I thought that was mainly if one had problems getting the soundcard to work. But I'll try these steps as well. 
Thanks for the help so far!

---

### Post by bogoliubov on 2007-08-09
Ok, so I tried the last steps as well, but no change. The sound keeps bugging med, and when I've almost decided to return the computer, it disappears! I have no idea why. It doesn't seem to have anything to do with how I connect the computer. Also, if I quit X, I can still hear the sound...

> **buntunub said:**
> When you reboot, make sure that the power chord is NOT connected. That should fix things. If not, again without the power chord attached, hibernate and then recover, and then reboot again. That should do it.

Hmm, why should this have anything to do with the noise?

---

### Post by fredj on 2007-08-10
The line you add to the /etc/modprobe.d/alsa-base file may work if you change it to
options snd-hda-intel position_fix=1 model=3stack
However you really need the correct line for your soundchip. Open a terminal and type
sudo cat /proc/asound/card0/codec\#*
The first line of output from that should give you the name of your soundchip. Then do a search
in these forums to see how other people have corrected this problem. I had exactly the same 
problem as you and fixed it completely by adding the above line to my alsa-base but sometimes
different lines are needed for different soundchips. My soundchip is an AD1896A.

---

### Post by bogoliubov on 2007-08-10
> **fredj said:**
> The line you add to the /etc/modprobe.d/alsa-base file may work if you change it to
options snd-hda-intel position_fix=1 model=3stack
However you really need the correct line for your soundchip. Open a terminal and type
sudo cat /proc/asound/card0/codec\#*
The first line of output from that should give you the name of your soundchip. Then do a search
in these forums to see how other people have corrected this problem. I had exactly the same 
problem as you and fixed it completely by adding the above line to my alsa-base but sometimes
different lines are needed for different soundchips. My soundchip is an AD1896A.

But the soundcard works; I can play music etc. I did do these last steps, but there are three different models that may be correct for my computer. So I guess I can try each one in turn and see if anything happens...

---

### Post by fredj on 2007-08-11
Yes try them all.

---

### Post by makito on 2008-07-22
I had the same issue with the same laptop (Clevo M540N). The buzzing went away just before I decided to return it. 
Right now I am having major problems with suspend, did you have any problems with that?

---

### Post by bogoliubov on 2008-07-23
Oh my, I thought I was the only one in the world with Clevo M540N and Ubuntu. Well, I have some threads on this forum about suspend; and I recently submitted a bug report on Launchpad.

The noise, I realized, is not really from the soundcard at all. Probably from the HD or from some capacitor on the mainboard. 

Anyway, I can suspend and resume by choosing suspend from the Gnome Menu, or pressing the power button. But if I use the lid, the computer usually crashes. 

What problems are you experiencing?

By the way; my laptop is really noisy (fan), is it the same for you?

---

