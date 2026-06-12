---
title: "Default microphone changes whenever headset is unplugged and plugged back in"
date: 2020-03-20
forum: Hardware
---

### Post by rogergodzilla99 on 2020-03-20
I have a Blue Snowball usb microphone that is almost always plugged in, a built in microphone, and a usb headset that has a microphone and speakers.

As it currently stands, the computer seems to favor whatever was plugged in most recently, but I want it to have a priority based on which devices are plugged in (ie snowball if it's plugged in, then the headset mic if the snowball isn't plugged in, then the integrated mic if neither of the external ones is plugged in).

Any ideas on how I can set this up?

Thanks in advance!

---

### Post by TheFu on 2020-03-20
That is a great question.  I&#8217;ve been lazy and just unplug and replug my Samson mic when i want it to be primary.
Google found ths:
[https://askubuntu.com/questions/1154586/how-can-i-change-pulseaudio-port-priorities](https://askubuntu.com/questions/1154586/how-can-i-change-pulseaudio-port-priorities)
and
[https://askubuntu.com/questions/113704/make-pulseaudio-prefer-external-audio-device](https://askubuntu.com/questions/113704/make-pulseaudio-prefer-external-audio-device)

More that you or I want to know:
 [https://wiki.archlinux.org/index.php/PulseAudio/Examples](https://wiki.archlinux.org/index.php/PulseAudio/Examples)

When we control settings via text config files, the distro doesn't matter.

---

### Post by rogergodzilla99 on 2020-03-23
Thank you so much!

I'm still having trouble, but I'm sure I can figure it out now that I have an idea of where to look.
The hardest part about solving most of the problems I get is knowing what to google.

I'll mark this as solved in the mean time.

---

### Post by rogergodzilla99 on 2020-03-23
I seem to have replied to my original post instead of to you... oops...

Thank you so much!

I'm still having trouble, but I'm sure I can figure it out now that I have an idea of where to look.
The hardest part about solving most of the problems I get is knowing what to google.

I'll mark this as solved in the mean time.

---

### Post by TheFu on 2020-03-23
I found the best answer is to use pavcontrol, the tab on the far right is "Configuration" - in that tab, have only 1 input (mic) and only 1 output (speakers) enabled. Any other devices should be "Off".  This will remove the undesired devices from the other tabs and with only 1 choice, things sorta "just work."

This assumes that pulseaudio (the daemon) is working correctly and that devices are connected.  Sometimes I've had to disconnect then reconnect my "headphones" ... which is a front-port jack that goes to speakers to get that jack seen by pulse.

I have these devices:

* Plantronics 7.1 headphones with mic (usually want to use it in duplex mode - both as output and input (mic)
* Samson USB Mic (always input/mic mode)
* Logitech C920 webcam + mic (can be webcam only or input/mic or both though the video isn't part of pulse at all)
* "headphone jack" cheap speakers (sometimes needed disconnect and replug the 2.5mm jack)

When they are all connected, the trick is recognizing which I want specifically to be used for the mic and which I want for output.  

And sometimes chromium gets confused because it likes to exclusively lock devices for use by the browser, though not always. The fix for that, for me, is to close chromium, kill pulse (pulseaudio -k), then restart pulse (pulseaudio -D), then restart chromium BEFORE firing up pavcontrol.  Pain. Most definitely.

---

### Post by rogergodzilla99 on 2020-03-24
That is what I finally settled on. I used that pavcontrol
Configuration > (headset device dropdown box) > analog stereo output
This made the computer not even look for a mic on the headset (from what I understand) which solved the problem 100%!

---

