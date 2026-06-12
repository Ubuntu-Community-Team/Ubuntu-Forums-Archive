---
title: "HP Pavilion dv7-1450us: Easiest setup ever!"
date: 2010-01-16
forum: Hardware
---

### Post by JeffRosenberg on 2010-01-16
I've just finished configuring my new HP Pavilion dv7-1450us, and wanted to report for those thinking of buying one that it was the easiest setup I've ever done!

I'm using the 64-bit version of Karmic, and everything has worked out of the box. Power management, touchpad, keyboard shortcut keys, and even (gasp) wireless worked without me having to touch anything. What a pleasant change from the Gateway computer I bought a few years ago.

There's been only one thing I've needed to do to get everything working: Install the proprietary ATI drivers to be able to use Compiz and special desktop effects. This went super-smoothly using Envy.

Just install, either using Synaptic or in the terminal:

```
sudo apt-get install envyng-core
```Then run Envy. You'll need to use the terminal for this:

```
envyng -t
```That will bring up a menu -- choose option 3 to install the ATI driver, restart your computer and you're good to go!

To anyone considering this computer, I've only been using it a short while, but so far I would highly recommend. I was up and running with practically no work whatsoever.

---

