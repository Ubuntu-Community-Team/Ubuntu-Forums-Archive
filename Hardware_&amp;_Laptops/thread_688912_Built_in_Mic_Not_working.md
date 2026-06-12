---
title: "Built in Mic Not working"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by cr4z3d on 2008-02-05
Just installed and updated Ubuntu 7.10 and sound works fine but I can't get my Mic working at all. It's a built in one on my ACER TravelMate 8200. I know it uses Intel High Definition Audio and I'm trying to configure all my sound with ALSA. I've tried testing the Mic through System > Prefs > Sound and clicking the test button next to Sound capture and it returns this error 

> 
gconfaudiosrc ! audioconvert ! audiosample ! gconfaudiosink profile=chat: Could not open resource for writing


I also tried out Sound Recorder and got this error:

> Your audio capture settings are invalid. Please correct them in the Multimedia settings.

In the sound settings I tried all the options in the drop down and they all gave similar results. 

I'm pretty new to linux in general so maybe it's something simple I couldn't figure out.. but I can tell you that in the Volume Control It's got options for HDA Intel (ALSA Mixer) and Realtek AC883 (OSS Mixer).

One thing I did notice though, I was able to unmute and raise the volume of the microphone in the HDA Intel mixer and sound came through the speakers.. So I'm not really sure what to do to get the mic working to record things.

---

