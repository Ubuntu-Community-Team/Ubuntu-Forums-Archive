---
title: "Nouveau causing a black screen in 11.04"
date: 2011-07-14
forum: Hardware
---

### Post by ivkowalenko on 2011-07-14
Quick background:

[LIST]
[*]The laptop is an old Toshiba Satellite with an NVIDIA GeForce2 Go, which uses driver versions 96.43.xx (the ones currently broken with modern Xorg builds)
[*]NVIDIA's own drivers don't work (surprise) with the modern Xorg builds.
[*]The system is intended to merely by a MythTV backend, and is basically just grabbing a bitstream out of a USB interface, so we don't need to worry too much about this looking pretty, or decoding HD video or anything.
[/LIST]
Nouveau is throwing me to a black screen pretty much as soon as it loads, including on the tty. I know the machine is working, since I can SSH in with absolutely no problem. If I get nouveau not to load, I can work the terminal, but Xorg won't start. I can switch to nv or vesa, but the MythTV configuration tool requires a working X session that, for some odd reason, needs some kind of functional (or existent) vdpau API (presumably saying "I can't do vdpau" will be enough, since I'm just configuring the software, and not actually decoding any video), and neither nv nor vesa seem to satisfy those library calls.

Any ideas? Or what I should do to get additional debugging information?

---

