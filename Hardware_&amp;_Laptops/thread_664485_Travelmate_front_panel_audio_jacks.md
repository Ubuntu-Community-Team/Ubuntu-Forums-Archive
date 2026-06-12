---
title: "Travelmate front panel audio jacks"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by Vince-0 on 2008-01-11
I'm having trouble getting the front panel audio plugs to work when I insert my headphone plug.

I have a Acer Travelmate 5720G, I believe it has an intel HD type on-board sound card

Here is the aplay -l output:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

The built in speakers work great, but no output through the headphones at all. I've looked at getting other ALSA drivers, but its already running off some kind of ALSA drivers.

I've searched high and low for some info but alas, no results.Is this a driver problem or is it just some settings I'm missing?Any suggestions would be freakin awesome!

Whoot Ubuntu!

---

### Post by eggdeng on 2008-01-11
This is a well-known routing problem with a lot of Intel HDA and VIA cards. 
To try for a quick fix
Open the the config file for editing
```
sudo gedit /etc/modprobe.d/alsa-base
```
Add the line
```
options snd-hda-intel model=acer probe_mask=1
```
to the bottom of the file. Save and reboot for changes to take effect.
For more help, see [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")
As the fix in each case is specific to the make and model of laptop, searching for your model on the forum will yield results.

---

