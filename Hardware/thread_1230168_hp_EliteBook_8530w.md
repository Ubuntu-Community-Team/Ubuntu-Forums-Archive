---
title: "hp EliteBook 8530w"
date: 2009-08-03
forum: Hardware
---

### Post by iKevin09 on 2009-08-03
I'm running an hp EliteBook 8530w. 50GB dedicated to Ubuntu Jaunty and the other 100GB dedicated to Windows XP Professional for college. It's setup as a dual-boot system. The specs that I'm about to list are my laptop's specs. I was wondering if there was something extra that I needed to download in order for all the components of my laptop to be utilized by Ubuntu Jaunty. Thanks!!

Intel Centrino 2 T9400 2.53GHz
nVidia Quadro FX 770m
Lightscribe DVD +/- RW
HP Webcam

Firefox's performance is very weak. When changing volume settings on the touchpad I have on my laptop, Ubuntu responds extrmely slowly.

I do have the restricted drivers enabled and is now running the native resolution of 1920x1200.

Any help at all would be greatly appreciated!!

---

### Post by pastalavista on 2009-08-03
Do you mean touchpad gestures or with the pointer control of volume applets? Or do you mean harware media controls?

---

### Post by iKevin09 on 2009-08-03
Yes, the touchpad gestures. I notice that when I'm touching the mute button on the touchpad, it turns red but then Ubuntu doesn't process it and still doesn't mute. The sound is off though, so I don't know what's happening there.

When sliding my finger on the volume controls on the touchpad, Ubuntu has several seconds of lag, and refreshes every half second, which gets very, very annoying.

I don't know if the built-in webcam would work with Ubuntu or not.

As I stated before, but when uploading pictures to Flickr, Mozilla and Opera (I've tested both) stops responding and turns to a grayscale until the upload is finished.

Thank you, pastalavista for your prompt response.

---

### Post by pastalavista on 2009-08-03
The problem is probably either the touchpad driver or the xorg.conf.. I think. Your system seems pretty new. Are you running 64-bit Ubuntu? What restricted drivers do you have active or available? Have you looked at the System->Preferrences->Mouse applet?

---

### Post by iKevin09 on 2009-08-03
I'm running 32-bit Ubuntu right now. I meant the black touch-sensitive bar above the keyboard. Where it has touch wireless toggling, mute toggling and volume up/down sliders.

How about the performance issues?

---

### Post by iKevin09 on 2009-08-03
Bump... Assistance anybody?

---

### Post by pveurshout on 2009-10-31
Hey, I also own an 8530w. I don't know whether this helps, but anyway:

Mute button: I always assumed this was only supposed to mute the internal laptop speakers (so just to control hardware).

Volume slider: in my case it can't be used the same way as in Windows. Instead of 'sliding' from the left to the right (or vice versa) you just have to hold your finger on either its left or its right side in order for the volume to go down/up.

Performance: I have a slightly different processor (T9600) and never had any performance issues, but perhaps you could try adding the "CPU Frequency Scaling Monitor" to your panel (right-click -> Add to Panel), then left-click it and set it to 'Performance' (I've read a thread somewhere about someone having problems with this where fixing the CPU frequency solved the problem).

I don't know if I'm just repeating stuff you already know/tried, but since this thread has been dead for a while I thought I'd just reply even though I'm no expert. And if it doesn't work you could of course always give Karmic a shot :)

---

