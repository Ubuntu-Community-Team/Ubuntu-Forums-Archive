---
title: "Problems with audio and earphones"
date: 2010-03-22
forum: Hardware
---

### Post by CoffeeCoder on 2010-03-22
This is a rather annoying problem.

For some reason, when I plug my headphones into the jack on my laptop, the audio STILL comes out of my main speakers as well as the headphones. I tried out another pair of headphones just to make sure it wasn't them that was the problem, but the problem still persisted. I just want to listen to music through my headphones...:|

I tried going through all of the sound settings and reading through the Ubuntu help files, but couldn't find anything on the subject. My audio card is an Intel High-Definition Audio Input/Output card. I tried looking up the driver in the "Hardware Drivers" tool, but absolutely no results came up for anything. 

Can anybody help me through this, please?

---

### Post by Yellow Pasque on 2010-03-22
It's called "jack sensing" and it can often be fixed by specifying a model keyword in /etc/modprobe.d/alsa-base.conf
See this for instructions: [http://ubuntuforums.org/showpost.php?p=8571901&postcount=6](http://ubuntuforums.org/showpost.php?p=8571901&postcount=6)

If none of the keywords work, you might want to try the latest ALSA drivers: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

If that doesn't work, you'll probably need to file a bug and/or get an alsa dev to look at the gory details of your audio hardware.

---

### Post by CoffeeCoder on 2010-03-23
Thanks for the reply and help!

This is what I got with the *aplay -l* command:

```
jeremy@Ubuntu-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I'm confused because it doesn't give me an exact model number/name to use in the next few commands. I do know that I have an HP G60-549DX laptop if that helps. 

Also, I'm confused by your next steps here...

> 
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add a line like the following:
```
options snd_hda_intel model=hp-dv5
```

Do I want to insert the "options snd_hda..." line into the gedit text file somewhere (and if so, where?), or do I want to enter that line into the terminal? 

Thanks for the help so far!

---

### Post by Yellow Pasque on 2010-03-23
Yes, you would append the line to the end of the alsa-base.conf file. You have some sort of Conexant chip and some quick searching shows me that your model is very similar to the g60-530us, so if I had to take a wild guess, I would try:
```
options snd_hda_intel model=laptop-hp530
```

You may also want to try a few other keywords. See: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#257](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#257)

---

### Post by CoffeeCoder on 2010-03-23
Thanks! Unfortunately it doesn't appear as though my sound card is supported entirely. Looks like I'll have to wait a bit; maybe I'll have better luck with Lucid Lynx when it comes out next month.

I managed to pull this information up when running the aplay -L command, though:

```
    HDA Intel, Conexant Digital
    IEC958 (S/PDIF) Digital Audio Output

```

I didn't see any matching model numbers in that list you linked me too, though. Google didn't yield good results either, it kept taking me to sites complaining about issues with Lenovo laptops, not HP.

---

### Post by dmzamora on 2010-03-24
I have the same problem with my Dell Vostro 1014. I did a wubi install the other week then it failed, we thought it was just because of the wubi (audio problem). My friend suggested i do a native install, still the same problem. 

I hope to fix it soon though. (still looking for solutions)

---

### Post by Yellow Pasque on 2010-03-25
> **dmzamora said:**
> I have the same problem with my Dell Vostro 1014. I did a wubi install the other week then it failed, we thought it was just because of the wubi (audio problem). My friend suggested i do a native install, still the same problem. 

I hope to fix it soon though. (still looking for solutions)
I've seen positive reports for the vostro 1014/15 when updating to the latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by CherryJoe on 2010-03-26
Check the input and out put jacks of your systems....Because when the problem with the jack port only then there is a problem with the ear phones or plugs of the laptops....Check onse the audio and video derives of the system.

---

### Post by bretteroo on 2010-04-07
I have an HP G60-630us and it does the same thing.  Plug headphones in to jack, but get sound through both speakers and headphones.

I have tried all the fixes above, except for the alsa upgrade, and scoured other pieces of the internet for help (all of which say pretty much the same thing).

What is frustrating about this for me is that pretty much everything else on this laptop works with ubuntu, even the web cam (in fact the only thing I have found so far that doesn't work is some of the function keys and the wifi on off button).

---

### Post by lidex on 2010-04-21
> **bretteroo said:**
> I have an HP G60-630us and it does the same thing.  Plug headphones in to jack, but get sound through both speakers and headphones.

I have tried all the fixes above, except for the alsa upgrade, and scoured other pieces of the internet for help (all of which say pretty much the same thing).

What is frustrating about this for me is that pretty much everything else on this laptop works with ubuntu, even the web cam (in fact the only thing I have found so far that doesn't work is some of the function keys and the wifi on off button).

Do this for me please. Had positive results on another G60.
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-vostro enable_msi=1
 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by CoffeeCoder on 2010-04-23
Hi guys, sorry I haven't responded in a while; I've been busy and hardly had time to use Ubuntu. 

Anyway, I'm going to wait until the new version comes out in six days. Once I've upgraded to 10.04, I'll report whether or not my speakers work properly. Thanks for all of the help so far, and hopefully everything will work properly in 10.04! :)

---

