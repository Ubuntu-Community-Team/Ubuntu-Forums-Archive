---
title: "Ubuntu on a tablet?"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by nala on 2006-06-13
I have a Toshiba R15-s829 and I would love to put Ubuntu on it. Judging from experience with the live CD, slate mode support is not built in. How can I set up support for handwriting recognition, using the stylus, flipping the screen and so forth, or is that possible?

---

### Post by Belathor on 2006-06-14
A Gnome developer has started a project on fundable.org to build an open source hand writing recognition engine. Here is the link to that:
[https://www.fundable.org/groupactions/handwriting-recognition-engine/]("https://www.fundable.org/groupactions/handwriting-recognition-engine/")

If you check planet.ubuntu.com you'll find that Og Maciel is messing around with a HP TC1100.

You can get the stylus to work using sudo apt-get install wacom-tools (at least that worked for me). You should be able to rotate the screen by opening a terminal and typing xrandr -o left (or right; whatever direction you want) but I haven't had much luck with it yet.

[Here]("http://gtt.blaubeermuffin.de/Main_Page") is a neat site that I found just a few days ago. I think it is by the same guy who is making the handwriting recognition engine.

There you go. I hope I am of some help. I have a Lenovo X41 Tablet and have been experimenting with Ubuntu as well. I also put a spec in for Edgy, but I messed up the spec name and have to get them to change it. Grrr... I really need to get some sleep!

Cheers!

---

