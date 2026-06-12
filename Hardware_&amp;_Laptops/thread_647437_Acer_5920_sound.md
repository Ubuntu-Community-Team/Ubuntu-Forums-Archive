---
title: "Acer 5920 sound"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by Bartender on 2007-12-22
Acer 5920, not the "G" model.
Attached a .jpg of the GUI controls.

It's an Intel sound chip.  The Acer has some sort of Dolby Virtual Surround, at least in Windows.  Lappy speakers sound fine with Vista.

In Ubuntu, headphones sound fine - two channel is balanced.  But the lappy's built-in speakers aren't right.  Playing a CD, the right-hand speaker makes all the sound.  Left-hand speaker, nothing at all.  Under "Sound Preferences" (shown in attachment) it doesn't seem to matter if I choose PCM, Front, or Surround under Devices.  Don't understand what I'm changing with that function.  The "test" button drives the left speaker, but it's only half the right speaker's volume.

Sound Playback is "Autodetect" in the screenshot, but set to ALSA behaves the same.

In the "Volume Control" window, PCM controls the output, even if I'm playing a CD.  The CD sliders don't seem to do anything.
And the headphone "on" or "off" switch on the next tab doesn't seem to do anything either.  I get lappy speaker output with the headphones connected regardless of switch.

Where do I start fixing this?

---

### Post by pizpot on 2008-02-11
I've got the same laptop. I had to open up the volume control and show the slider for Center, and now my sound works.

---

### Post by rishubhai on 2008-02-13
I am also using the same laptop and facing the same problem,
how do i "show the slider for Center" ??

---

### Post by Bartender on 2008-02-13
Hi, rish -
Right-click on the little speaker applet in the upper right corner.  Left-click on "Open Volume Control".  Left click on "Edit". Left-click on "Preferences".  Put a checkmark beside every device in the list and close the list.  This will give you sliders for all those devices.  Crank "Center" up.

This didn't work for me.  Volume still on right side only.  But worth a try!

---

### Post by rishubhai on 2008-02-16
I did try clicking on all the options in the volume control, but still the main volume control (the hardware on the front face of the laptop) does not seem to have control over the master volume control (the software). Its only one channel (i m not sure whether its right or left) that is controlled by the (hardware) controller. 

Also the 'Fn' (function) key for volume (mute / unmute) does not work effectively.

Is there a way to fix this??

---

### Post by Once&amp;Done on 2008-03-10
Just wanted to chime in that for me the key slider was the Surround slider.  None of the others seem to make the slightest difference (playing music from the HD) but the Surround slider set all three speakers giving me my music.  One step closer to a fully working system. :-)  Has anybody managed to get the volume spinner on the front to work?  That's my next  thing to research.

---

