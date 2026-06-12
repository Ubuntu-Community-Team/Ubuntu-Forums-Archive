---
title: "Volume Buttons control microphone input volume"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by El Viejo Lobo on 2007-04-25
I had no microphone input after installing Feisty on a Presario V2000 I solved the problem
some how with alsamixer.
I got my surprise when I tried to change volume and noting happen. The buttons control the mic's 
input volume and mute. I could not find anything about it over Google or Forums.
Is there is any way to tell the laptop to fix it?

Here is the thread about the Mic's problem after Feisty install.
[http://ubuntuforums.org/showthread.php?p=2510974#post2510974](http://ubuntuforums.org/showthread.php?p=2510974#post2510974)

---

### Post by theheadlessrabbit on 2007-12-10
I am having the exact same problem.

After getting a microphone and messing around with the volume settings (I didn't even touch the terminal) i got the mic working perfectly, but when I tried to change my systems master volume with the volume control buttons on my laptop, my mic volume changed instead of the master volume.  and I don't know how to fix it.  (I dont know how I broke it, either)

---

### Post by coskierken on 2007-12-10
Right click the volume control and go to preferences.  You get to pick what the volume action controls.  You can use Headset or PCM, or whatever else you want that is one the list.  Oh, I have found the GNOME-alsamixer to be better.  Just my opinion.  :lolflag:

---

### Post by theheadlessrabbit on 2007-12-11
I don't mean to sound rude, but that was one of the first things I tried.

When I right click and select Preferences, I have both the Realtek ALC262 (OSS Mixer) and the HDA ATI SB (Alsa mixer) to choose from.  

 ATI SB is the one that i have selected.  

 I have "master" highlighted as 'the device and track i want to control', but my laptop's volume buttons still control the mic volume, not the master.

I do appreciate the help.  is there anything else i should try?

---

### Post by growse on 2008-04-10
No dice here as well. Setting it to PCM in the preferences just gets reset when I next open the preferences. Grrr....

---

### Post by coewar on 2008-07-08
I also have exactly the same problem. I managed to get it working perfectly in KDE though; the mic and the volume always worked with the master volume.

Only after I started messing with mic in Gnome, did my vol controls switch to controlling that. However, I don't actually have the mic working in Gnome yet.

I just stumbled on the solution!!!

The thought of right-clicking on the vol and selecting the "device to track" was in the right thought.. but wrong area.
You want to go to "System->Preferences->Sound" then you'll see tabs: "Devices, Sounds, System beep" and in "Devices" near the bottom you'll see: "Default Mixer Tracks".  There, you select your "Device" (like Alsa mixer) and then in the list, you'll probably notice "Microphone" is selected. So in that list, select "Master" or whatever you want, and the vol controls will control it.

---

