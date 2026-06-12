---
title: "S-Video on compaq nx9110 doesn't work"
date: 2009-01-20
forum: Hardware
---

### Post by Kumagoro on 2009-01-20
I recently installed Ubuntu 8.10 on this HP Compaq nx9110

It works fine, the volume/mute buttons work, USB ports work too.

The only problem is S-Video, I wanted to plug this into my TV to watch some movies. It worked flawlessly on Windows, but I can't get it to work on Ubuntu

The Ubuntu I use is a modified polish version from [www.ubuntu.pl](www.ubuntu.pl)

I try to go to System/Preferences/Resolution, but it doesn't see the other screen, just the "laptop"


I connect PC with the TV by an ordinary S-Video cable.
The laptop has got and ATI Mobility Radeon 9000IGP graphics card

---

### Post by Kumagoro on 2009-01-21
Ok sorry for bumping but here's what I figured out.

I heard that making X use the default VESA drivers solves the problem.

However, I think VESA = no 3d = no composite desktop, and I'm addicted to Compiz :P

Is there any way to like switch between configs so that I can change between VESA and open ATI drivers with a simple console command?

---

### Post by cnich23 on 2009-03-17
I played around with trying to accomplish svideo output for a long time with no success on this exact machine, as far as I could get was display of terminal login.  I had to end up dual booting.  Still would be interested in a fix or solution for the vcard

---

