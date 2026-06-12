---
title: "nvidia upgrade gone horribly wrong"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by Feanor93 on 2009-09-24
Hello,

I was upgrading my computer the other night, and among other things, I installed a Zotac nVidia GeForce 9500GT video card. When I boot to Ubuntu, everything looks fine until I log in and there's a big white screen staring me in the face. I can tell that something is going on behind it, because the cursor changes when it's over the places where Pidgin's edges should be. I've tried going into recovery mode and choosing the auto-fix for graphics, but that doesn't work. Any help would be appreciated.

Thanks,
Feanor93

---

### Post by rreese6 on 2009-09-24
We need  more information.
What Revision of Ubuntu are you using 8.04, 8.10, 9.04?
tell us more about what upgrade you were doing..
What desktop KDE, Gnome..etc?
What was your old video card?
can you attach the /etc/X11/xorg.conf file here?

It appears that you should boot off of your liveCD to get the information to post it here.
Once we know more about your problem, the better we will be ale to help you.

---

### Post by Feanor93 on 2009-09-24
Sorry, I'm using Ubuntu 9.4. I was basically giving my computer a complete overhaul with a new motherboard, processor, sound card, and ram, as well as the video card.  The processor is an Intel core duo 3.0Ghz. To be exact, I'm using GNOME 2.26.1. My old video card was an ATI Radeon 9600 pro with 256mb. As for the xorg.conf file, I'll attach it.

Thanks for the prompt reply!
Feanor93

---

### Post by gradinaruvasile on 2009-09-24
> **Feanor93 said:**
> Sorry, I'm using Ubuntu 9.4. I was basically giving my computer a complete overhaul with a new motherboard, processor, sound card, and ram, as well as the video card.  The processor is an Intel core duo 3.0Ghz. To be exact, I'm using GNOME 2.26.1. My old video card was an ATI Radeon 9600 pro with 256mb. As for the xorg.conf file, I'll attach it.

Thanks for the prompt reply!
Feanor93

Did u install the proprietary nvidia drivers?
Your xorg,conf is not complete.

Edit: Should be soething like the one i attached.

---

### Post by Feanor93 on 2009-09-24
I tried a solution from another thread, typing [FONT=Courier New]sudo killall compiz.real [/FONT]into the command line. The white went away, but the tops of all the windows were gone. I signed out and then back in, and it seemed to work fine (except for the fact that compiz is not working anymore). 

What should I do from here? Should I install the nvidia drivers? Should I reinstall compiz? Or should I edit my xorg.conf file like gradinaruvasile suggested?

Thanks for your help,
Feanor93

---

### Post by gdonwallace on 2009-09-24
My first suggestion would be to start up Synaptic and install the propitiatory Nvidia video drivers.

If you xorg.conf file does not list nvidia as the adapter name, then installing the drivers will help.  I would also suggest installing Nvidia Xserver Settings.  This will give you a way to make changes to the card settings that are then saved to the xorg.conf file.

If you continue to have problems after this, you may need to get out to Nvidia website and see if they have any linux drivers for your card.

Good Luck.

---

### Post by Feanor93 on 2009-09-24
Do you know what the name of the NVidia drivers are(like in synaptic)? How do I get the nvidia xserver settings?

Thank you for your answers,
Feanor93

---

### Post by rreese6 on 2009-09-24
I found this on another site

```
   1. Run Applications/Add/Remove
   2. From the left menu choose System Tools

   3. Next from the right menu, find and select for install: Desktop Effects 
(Compiz Setup) and Nvidia binary X.org Driver. By selecting the driver you 
will get the list of supported graphics card.

   4. Click Apply Changes and after installation go to System/Administration
/Hardware Drivers

   5. The system will search for available drivers and you can choose the 
recommended option from the list to activate the driver by clicking Activate 
button.

   6. Next, restart your system and the new nVidia graphic display driver will 
be on use.

   7. To enable the desktop effects on Ubuntu 9.04, go to System/Preferences
/Appearance and on the Visual Effects tab choose Normal or Extra if you have 
never graphic system.
```


Hope this helps you.

---

### Post by rreese6 on 2009-09-26
**bump**

---

### Post by Feanor93 on 2009-09-28
Sorry, I thought that I had already replied to this but I guess I didn't. Anyways, my card is working great now!

Thanks for your help! I couldn't have done this without you.
Feanor93

---

