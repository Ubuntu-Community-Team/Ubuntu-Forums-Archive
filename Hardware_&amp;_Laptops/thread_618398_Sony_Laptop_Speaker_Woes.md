---
title: "Sony Laptop Speaker Woes"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by Sullview on 2007-11-20
I've seen others with similar problems, but I haven't found a solution that works yet.

Okay, some background: I'm extremely new to using Linux and I'm still getting my bearings. I've installed 7.10 and it installed perfectly, no problems except for this one. I'm using a Sony VAIO VGN-FZ140N, a model for which there appears to be little testing or support. Sound comes out of my laptop's speakers just fine, but when I plug in headphones or external speakers, nothing happens. The laptop speakers continue to play, but don't mute, and no sound comes out of the device. 

Both my speakers and headphones work great on Windows, so I'm not really sure what the problem is. I tried messing around with the settings in my sound, but that didn't accomplish anything. I suspect that I'm going to have to do something pretty complicated to solve this, but I'm just a beginner and I don't know what that might be. Can anyone help?

Thanks in advance,
Nick

---

### Post by hzsolti on 2007-11-23
Hello,
there many topics for this problem... ;)

So at first complile the newest alsa, and plugins for it...
[**alsa-driver-1.0.15**]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2")
[**alsa-plugins-1.0.15**]("ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.15.tar.bz2")

when you are ready with this
you should open the terminal...
and type this:
```

sudo gedit /etc/modprobe.d/alsa-base

```

Add to the end of the file this line:
```

options snd-hda-intel model=vaio

```

Last step is installing the GNOME ALSA MIXER....
from Application->Add/Remove

Lauch the GNOME ALSA MIXER
You will see 2 checkboxes on the bottom:
- Mic Jack
- Internal Mic

Select wich you want to use....
And now restart your VAIO :)

If I write something you can't understand just write... :)

---

