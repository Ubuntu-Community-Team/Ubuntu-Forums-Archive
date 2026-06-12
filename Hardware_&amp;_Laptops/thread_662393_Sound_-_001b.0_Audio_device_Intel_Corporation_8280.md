---
title: "Sound - 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Control"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by oiper on 2008-01-08
I've about as confused as I could be. I have a ThinkPad R61i.

The lspci | grep Audio command yeilds:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

I have tried installing alsa-1.0.15rc1 from source. It didn't work. Various forum posts have pulled me this way and that. Any idea on whether the sound for this card with work? The live CD for Ubuntu had sound. So I know it "can" work.

My /etc/modprobe.d/alsa-base file currently has: 
```
options snd-hda-intel model=laptop-eapd

```

I've tried lots of options there. I'm very lost. Does anyone have this working with Gusty? :confused:

---

### Post by Yellow Pasque on 2008-01-08
If you can't get it working with ALSA, try OSSv4 (link in sig). Also, why did you use the release candidate version (1.0.15rc1) when the actual release (1.0.15) is out?

---

### Post by oiper on 2008-01-09
Thanks for the reply. I got to step 7 for OSSv4. Now I can't log in to Gnome. It gives me a "session lasted less than 10 seconds" error.

The alsa version was used according to a guide I was following, which was posted after the final release. So I assumed there must be a reason to use rc1.

---

### Post by oiper on 2008-01-10
I uninstalled OSSv4. Reinstalled every package that was related to sound. Installed alsa-1.0.15 from source.

At this point, I could log in again. I put "options snd-hda-intel model=lenovo" at the end of my /etc/modprobe.d/alsa-base file.

Then I:
[LIST]
[*]sudo apt-get install linux-backports-modules
[*]depmod -a
[*]modprobe snd-hda-intel
[/LIST]

Then the most important step:

I had to press the physical mute button on my laptop. At this point sound started working. 

Note: My sound applet thinks the sound is muted, but it's not. The physical volume buttons do bring the indicator up on the screen, but the sound level does not change.

The headset works great. I don't have an internal mic. My Logitech Quickcam mic and the mic plug both work great.

Maybe this will help someone. 

I do not believe that installing alsa-1.0.15 was needed, just the backports modules. I could be wrong.

:guitar:

---

### Post by Deus42 on 2008-02-12
This worked for me on a Dell D630 (You were right, you do not need to install a different version of alsa)

Thanks a bunch, this helped me out more that you can imagine!

---

