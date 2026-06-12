---
title: "Synaptic pad not working"
date: 2010-09-12
forum: Hardware
---

### Post by gwu777 on 2010-09-12
Hi, A few month ago, my synaptic pad stop working on my ubuntu 10.04 system. I check all the setting under "mouse" and play around but nothing works. My usb mouse works fine. When I boot under windows, the pad works normally. The pad on and off button on the laptop has no effect.

Any ideas?

---

### Post by banquo on 2010-09-12
Hi!
Glad to see the thread, have the same problem on my gf's laptop, 
it started just some days ago.
It's a HP Pavilion, with Lucid.
No probs earlier. But now the pad doesnt work, however usb-mouse works fine. Keyboard probs sometimes , but never at startup it just occurs sometimes after some minutes of usage :S

---

### Post by gwu777 on 2010-09-14
Another bit of frustration. In fact I am coming back to work after a summer away from my laptop and find things are not working as they should... My sound isn't working, the card seem to be installed ok, the alsa plug-in seem ok, I just have no sound.

No sound, no mouse, it is starting to be annoying!

HELP! :(

---

### Post by gwu777 on 2010-09-14
I disqbled the automatic login. Mouse and sound work inside the gdm, they stop working when I have looged in. Any ideas?

---

### Post by gwu777 on 2010-09-15
> **gwu777 said:**
> I disqbled the automatic login. Mouse and sound work inside the gdm, they stop working when I have looged in. Any ideas?

forget about the sound, after screwing my system seriously, I reinstalled ubuntu and the sound is working, however the pad is still not working. Which lead me to the conclusion that the problem is in my home directory as I have kept it. furthermore if I create a new account the pad is working fine. What can stop the pad from working in my configuration?

Thank you very much for your help.

---

### Post by gwu777 on 2010-09-16
No-one has any ideas why my pad can work in one new profile and not in my original one? Please...

---

### Post by gwu777 on 2010-09-18
> **cariboo907 said:**
> 

You will have to use gconf-editor to edit/change any values.

> **doughless said:**
> 

Open gconf-editor, go to desktop/gnome/peripherals/touchpad, and check   the option touchpad_enabled. My touchpad immediately started  working.

This was the answer in another post I followed. for me touchpad_enabled wasn't  checked, now it is and it worked immediatly. Very  simple solution, but my laptop is now happy!

---

