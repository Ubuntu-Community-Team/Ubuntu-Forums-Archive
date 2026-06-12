---
title: "Logitech USB Headphones + Mic Do Not Work"
date: 2009-04-15
forum: Hardware
---

### Post by fidgaf on 2009-04-15
I had this issue with Hardy and it is the same with Jaunty (Beta).

I doubt it will change with the new release (but you never know), so can anyone help?

I have USB Logitech headphones with a build in mic (Clear Chat Pro with USB). They work perfectly with every sound application in Windows XP - Not at all (nearly) in Jaunty or Hardy.

They do not seem to be detected correctly.

No sound through the ear-pieces and no activity from the mic.

Oddly, activating the built in control for volume sends the volume indicator on the desktop nuts (flashing on, off, on, off etc.)

I did a search and changed *options snd-usb-audio index=-2* to *options snd-usb-audio index=-1* in alsa-base.conf :

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

It made no difference.

I cannot find a thread where this issue has been permanently resolved.

Can any one help, please?


.

---

### Post by Brucevdk on 2009-04-26
I didn't notice that you were talking about different device so I've split this post into its own thread. See: [Logitech ClearChat PC Wireless](http://ubuntuforums.org/showthread.php?p=7158515).

---

### Post by fidgaf on 2009-04-27
Mine are not wireless but I did as you suggested (not the wireless option)and yes, I do get sound.

I have no control over volume on the headset and no white noise or mic feedback.

Mic appears not to do anything.

---

### Post by tahirih on 2009-05-11
I just bought the Logitech ClearChat (non-wireless) as well and I have the same problem! The headphones put sound out but the mic seems to do nothing!

---

