---
title: "Sound coming out of only 1  speaker"
date: 2011-08-21
forum: Hardware
---

### Post by 8_Bit on 2011-08-21
I finally got sound to work in Kubuntu and have switched back to it from Lubuntu.

But now I have another problem. **The sound only comes out of _one_ speaker.**

I have done all sorts of tweaking and messing with the Phonon sound settings. Everything looks OK in the settings, but I don't see any options for adjusting the "Left" and "Right" sound channel balance. Is that normal? I only see one draggable volume knob.

What should I do? What commands should I run to get some good logs/data on the drivers?

I'm a huge noob when it comes to diagnosing hardware problems on Linux, please bare with me. On Windows  I would just go to the device manager and try to fix the drivers and such, but on Linux there's no such thing as a centralized GUI-based device manager from what I can see... And I really don't even know what kind of sound card I have. All it says is "Internal Audio Analog Stereo" in the sound manager and I see also "Analog Stereo Duplex" in the Speaker Setup tab.

---

### Post by gordintoronto on 2011-08-21
Are you confident that the plug is fully inserted, and that both speakers actually work? Do you have earphones you can try?

My rule of thumb: if it can be the cable, it's the cable.

---

### Post by 8_Bit on 2011-08-23
Both speakers work fine if I reboot the system and load up Windows 7, without ever even changing or touching the wires or speakers.

So yes, I'm sure. Thanks for trying to help though.

---

### Post by gordintoronto on 2011-08-23
Have you tried Alsamixer? It runs (graphically) from the command line, and can help identify if something is muted, which is the most common problem.

---

### Post by os2 on 2012-12-27
Did you manage to resolve this problem?

Both channels are routed to one speaker only. Headphones plugged in work fine in stereo.

---

### Post by howefield on 2012-12-27
Old thread closed.

---

