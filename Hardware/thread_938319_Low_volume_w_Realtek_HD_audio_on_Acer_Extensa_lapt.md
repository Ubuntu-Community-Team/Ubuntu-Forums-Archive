---
title: "Low volume w/ Realtek HD audio on Acer Extensa laptop"
date: 2008-10-04
forum: Hardware
---

### Post by geovino on 2008-10-04
I have a Realtek High Definition audio card on an Acer Extensa 4420 w/ AMD X2 chip. It's running on Mint 5 which is based on Hardy and it has very low volume even though the volume is fine in Vista on the other partition. 

What causes this? Anyway to fix it? i think its running ALSA for sound.

---

### Post by kubel on 2008-10-04
I have the same problem. 

Biostar TF560 A2+
Realtek ALC888
Ubuntu 8.04

Still looking for a fix.

EDIT: Also some static, but possibly due to my speakers being cranked up to 100%.

---

### Post by geovino on 2008-10-05
Also: when plugging in headphones, sound turns off altogether.

What would cause this?

---

### Post by kubel on 2008-10-05
Geovino, I think I found a fix. In my case, I did this:

1) Launch audio mixer (I used HDA NVidia Alsa Mixer). 
2) Go to Edit > Preferences.
3) Check everything on the list.
4) Click Close.
5) Start tinkering with the new mixers. In my case, "Surround" was nearly at 0% but when I cranked it up, up went the volume (even though I don't have surround speakers). Seems like a simple glitch, with a simple workaround.

The ones on my system that had an effect on overall volume were "Master", "PCM", and "Surround", so try those first. Also, I noticed that "Master" has only a partial effect on volume. When "Surround" is cranked too high, it causes static.

Hope this helps on your laptop too.

---

### Post by geovino on 2008-10-06
Thanks, I right-clicked on the speaker on the toolbar and in preferences checked off all. I did notice that Mic Boost was turned down.I now get some sound out of the headphones but its still low volume even when everything volume control that I see is up to 90% or more. there must be another volume control that set very low and I haven't found yet. I wonder where it could be?

---

### Post by toganet on 2008-10-19
I'm battling the same problem.  I have working audio with this card (as reported by aplay -l):

[CODE**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
][/CODE]

I have to crank the volume all the way on everything to get decent sound.  I suspect there is a missing volume control somewhere -- I don't have a slider for 'Surround' in my preferences, although my surround is working.

---

### Post by kingtiger01 on 2008-10-19
try Alsaconfig from terminal. there might be a missing Slider in the GuI.


Just Food For Thought.

~Kingtiger

---

### Post by NoWayBill on 2008-10-19
:arrow: Geovino

Do **lspci** in terminal.
If you get a line like this...

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

...your Extensa uses the Intel sound chip, try this...

> sudo gedit /ect/modprobe.d/alsa-base

Add this to the end of the file...

**options snd-hda-intel model=acer**

This corrected the sound issues on my Extensa 5620.

---

