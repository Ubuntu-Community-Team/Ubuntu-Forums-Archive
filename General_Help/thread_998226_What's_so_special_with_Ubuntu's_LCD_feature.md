---
title: "What's so special with Ubuntu's LCD feature ?"
date: 2008-11-30
forum: General Help
---

### Post by jcarnat on 2008-11-30
Hello,

Since I tried Ubuntu (the Ibex release), I'm trying to understand how the LCD font rendering was achieved. I googled and read about Apple/MS patent, freetype2 ftoption.h and quite a bit of more things.

I wanted to reproduce that (damm) nice looking on my NetBSD workstation.
I tried setting the SUXPIXEL and BYTECODE options in freetype2 but this wasn't enough.
I took /etc/fonts' content and font files from my Ubuntu install to my NetBSD install.
I checked Xorg's DPI and Gnome font configuration.

The closer I could get is:
[http://test.tumfatig.net/details.NetBSD.png](http://test.tumfatig.net/details.NetBSD.png)
[http://test.tumfatig.net/details.ubuntu.png](http://test.tumfatig.net/details.ubuntu.png)

[http://test.tumfatig.net/fonts.NetBSD.png](http://test.tumfatig.net/fonts.NetBSD.png)
[http://test.tumfatig.net/fonts.ubuntu.png](http://test.tumfatig.net/fonts.ubuntu.png)

I read about [http://david.freetype.org/lcd/](http://david.freetype.org/lcd/) but they seem quite outdated.

So tell me :) How exactly did you achieve that font rendering ? freetype2, cairo, libXft, more ?

TIA,
     Jo

---

