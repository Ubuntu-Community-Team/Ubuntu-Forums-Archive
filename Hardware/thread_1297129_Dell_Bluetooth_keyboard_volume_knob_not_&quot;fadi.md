---
title: "Dell Bluetooth keyboard volume knob not &quot;fading&quot; volume"
date: 2009-10-21
forum: Hardware
---

### Post by bond1973 on 2009-10-21
Running Ubuntu 9.04 on a Dell Latitude D830.  Also running a Dell BT keyboard without USB dongle (because laptop has BT built-in).  This used to work then suddenly stopped.  The volume knob used to allow me to incremently adjust the volume.  Now it's either on or off (the sound that is, via the knob on the keyboard).  Hoping this makes sense.  When I turn the knob I see the volume adjusting on the screen, but nothing happen to the actual volume.  That is until the very last "on-screen notch"...it'll then turn the sound off.  Again...I hope this makes sense.  Any thoughts?

Thanks
Rick

---

### Post by Giblet5 on 2009-10-21
Have you been adjusting the global shortcuts?

Click on System->Preferences->Keyboard Shortcuts.

Make sure that:

Volume up = XF86AudioRaiseVolume
Volume down = XF86AudioLowerVolume

---

### Post by bond1973 on 2009-10-21
I have been in there and reset those, though they were already like that when I went in there.

The knob does show volume control on the screen.  It shows me it's sliding the volume up and down, but there's no variation in the actual volume.  It's either on or off, not 50% even though I can set the slider to 50% via the knob.  

Thanks for the response.

---

### Post by Giblet5 on 2009-10-21
Have you been using a bluetooth headset?

On *my* laptop, using my Plantronics B510 headset causes the volume control's selected playback device to switch to the BT headset. When I turn the headset off, it does ... odd things.

I corrected it by removing pulseaudio and using the Alsa mixer.

Odd that you get all or nothing...


I don't think the BT keyboard has anything to do with it.

What happens when you open a terminal, and ```
alsamixer
```

Try installing it if you don't have it already...

When you change the master volume, does the audio level rise/lower correctly?

---

### Post by bond1973 on 2009-10-21
I have had my Plantronics V510 connected to my laptop in the past...used it for my tech support job with a HUD.  It's still showing as a BT device, though I don't use it any more and the that BT headset has croaked anyway.  I'll remove that.  

When I alsamixer at cmd it does show me a graphical display of sort, so it appears as though that's installed.  My "Volume Control" screen shows Alsa, OSS and Pulseaudio as options.

Everything else works fine.  Volume-wise I mean.  Volume slider and such.  I'll try removing the Plantronics for one...any other suggested changes to my setup from what I've told you?

Thanks very much
Rick

---

### Post by Giblet5 on 2009-10-21
> **bond1973 said:**
> I have had my Plantronics V510 connected to my laptop in the past...used it for my tech support job with a HUD.  It's still showing as a BT device, though I don't use it any more and the that BT headset has croaked anyway.  I'll remove that.  

When I alsamixer at cmd it does show me a graphical display of sort, so it appears as though that's installed.  My "Volume Control" screen shows Alsa, OSS and Pulseaudio as options.

Everything else works fine.  Volume-wise I mean.  Volume slider and such.  I'll try removing the Plantronics for one...any other suggested changes to my setup from what I've told you?

Thanks very much
Rick

No... I got nothin'.

I even tried using my Logitech BT keyboard to reproduce this. It just works...

---

### Post by bond1973 on 2009-10-21
Ehh...that's cool.  That could be the problem.  I'll know when I get into work tomorrow and try it out with the BT headset removed.  Thanks again and I'll be sure to respond whether it works or not.

Thanks Again
Rick

EDIT....I just played with the AlsaMixer (cmd) and noticed that adjusting that Master does nothing....PCM adjusts the volume properly though...thought I'd throw that in.

---

### Post by bond1973 on 2009-10-22
No go by removing the Plantronics.  I'll keep playin' with stuff for now.  Thanks for the input.

Rick

---

