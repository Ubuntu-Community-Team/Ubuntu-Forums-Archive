---
title: "[Natty] Logitech PS3/PC Headset Not Working"
date: 2011-04-16
forum: Hardware
---

### Post by Joomla12 on 2011-04-16
Awright, I need some help...I've got a Logitech PS3/PC headset that just suddenly stopped working after upgrading to the Natty beta. It was working for a while but the ear piece was really quiet. I installed Gnome Alsa Mixer to fix that. Fixed the ear piece volume, and it worked for maybe 10 minutes. Now the MIC is completely unresponsive but the ear piece still works. I've been Googling for an hour or so now trying different things but nothing's worked.

lsusb does show it though.

```
Bus 003 Device 003: ID 046d:0a01 Logitech, Inc. USB Headset

```

---

### Post by 4manifold on 2011-04-29
I have a similar problem, haven't found a fix yet.  I just upgraded to Natty and my headset no longer works.  I am using a Logitech Clear Chat Comfort USB headset.  It shows up in the Hardware tab in Sound Preferences, but it doesn't show up under either the Input tab or the Output tab.

It does show up also when I type lsusb in terminal.  The result is:
```
Bus 006 Device 005: ID 046d:0a0c Logitech, Inc. Clear Chat Comfort USB Headset
```

---

### Post by 4manifold on 2011-04-30
Well, this isn't that spectacular, but I restarted the machine with the headset plugged in, and now it works fine.

---

### Post by givemelove on 2011-05-03
I confirm I'm able to reproduce the same behavior. The controls won't appear in the sound menu in Natty. the Alsamixer will detect it though.

If we do restart the computer with the headset already ON, the controls will be made available and everything would work just fine.

---

### Post by mFacenet on 2011-05-12
Restarting the pulse server fixes this

run 
```
pulseaudio -k 
pulseaudio --check
```

---

