---
title: "Asus G2S"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by ema on 2008-01-13
Dear all,

I installed Ubuntu 7.10 on this brand new notebook.
Everything worked, everything automagically detected:

nVidia 8600M
Integrated output sound system
Bluethooth
Wireless adapter
Network adapter

What didn't worked out of the box is:

Webcam (I had to manually compile and install [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/))
Integrated microphones 

I have one Issue with the camera: the image is upside down. How to fix it?

What really annoys me is the lacking support for integrated microphones.
This is Alsamixer view for capture devices:
[[IMG]http://img135.imageshack.us/img135/6103/alsamixerfr9.png[/IMG]](http://imageshack.us)

What could be missing here would be **critical** for my future use of notebook. I need the microphone working...everything (apart the webcam that is upside down) is working without any glitches...

I hope someone can help,

Thanks in advance,
Ema.

---

### Post by Bartender on 2008-01-13
Since you're already into alsamixer you probly checked this but here goes:  Did you

Right-click on speaker applet in upper panel
Left-click on "Open Volume Control"
Left-click on "Edit"
Left-click on "Preferences"
Tick all the tracks to "on"?

---

### Post by ema on 2008-01-13
> **Bartender said:**
> Since you're already into alsamixer you probly checked this but here goes:  Did you

Right-click on speaker applet in upper panel
Left-click on "Open Volume Control"
Left-click on "Edit"
Left-click on "Preferences"
Tick all the tracks to "on"?


Yes I did... :-(

---

### Post by abeowitz on 2008-03-10
In Gnome, right-click on your volume button in the panel and choose preferences.

Make sure it's on HDA Intel (Alsa Mixer)

Close it

Right click again and choose "Open Volume Control"

Edit/Preferences.

Make sure "FRONT" is checked in addition to PCM, Headphone, Master...

Close

Slide the FRONT volume controls up.

(Note this works for me in Hardy, but the volume is weak, esp bass.)

Not sure what the deal with this is yet.  Still learning about ALSA & this G2S-A1 laptop...

Hope that helps.

---

