---
title: "open source hardware acceleration"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by az on 2005-04-22
As I understand it, Nvidia only offers binary drivers for their accelerated graphics cards, while ATI has some open source drivers for the older cards along with less reliable binary-only drivers for their newer stuff.

I want to avoid proprietary drivers, and I do not need to have the newest card on the market.  Is ATI the better choice for open source hardware acceleration?

---

### Post by simianMiscreant on 2005-04-22
Ohhhhh no no no no, heavens no. Enabling hardware acceleration on an ATI card in Linux can be **hell** for some users, and you'll almost never garner the same performance as someone using an nVidia card.

---

### Post by az on 2005-04-22
[QUOTE=simianMiscreant]Ohhhhh no no no no, heavens no. Enabling hardware acceleration on an ATI card in Linux can be **hell** for some users, and you'll almost never garner the same performance as someone using an nVidia card.[/QUOTE]

I though that it was only the proprietairy drivers that were unstable.  As far as performance, I only need to run tuxracer and maybe do the "wobbly windows" thing to impress the father-in-law...

So, it is possible to have hardware acceleration using only free open source drivers with _any_ card?

---

### Post by nautilus on 2005-04-22
VIA has released their drivers (3D accelerated) completely, including many (most) of the Savage-series chipsets, I think up until the Twister, which is still a pretty decent tuxracer/aqfh/etc. 3D card.

[http://lwn.net/Articles/131777/](http://lwn.net/Articles/131777/)
[http://www.viaarena.com/](http://www.viaarena.com/)

---

### Post by skoal on 2005-04-22
[QUOTE=azz]So, it is possible to have hardware acceleration using only free open source drivers with _any_ card?[/QUOTE]

Ahh...now I can offer an opinion.  I didn't have one before since I thought it was only older ATI cards you were interested in.  If not, the guys at XGI have 100% open source for their hardware accelerated line of video cards.

Check out their website: [http://www.xgitech.com/](http://www.xgitech.com/)

* Their website is slower than 2 turtles making love, but [here](http://www.xgitech.com/about/about_press1.asp?CTID={C3FD7D03-6BE1-4BB9-9F34-1221E723B87F}) is a recent press release you might find of interest.  About a year or two ago their windows performance was pretty sub par.  I'd be interested to see some benchmarks running these open source cards on Linux now.

---

### Post by az on 2005-04-23
Okay, thanks.

What about an older (really cheap) card.  Am I to understand, then that _all_ the open-source drivers for ATI are crashy?  As well, there are no such drivers for Nvidia older cards?

---

### Post by az on 2005-04-26
If I use this card:

nVIDIA RIVA TNT2 M64 PRO 16 MB PCI VIDEO CARD

Will the xserver nv and RIVA drivers provide stable hardware acceleration?

---

### Post by jdodson on 2005-04-26
[QUOTE=azz]If I use this card:

nVIDIA RIVA TNT2 M64 PRO 16 MB PCI VIDEO CARD

Will the xserver nv and RIVA drivers provide stable hardware acceleration?[/QUOTE]

the open source "nv" drivers provide no 3D acceleration that i am aware of.  being a nvidia user, i got really poor 3D performance out of my new gforce5400LE with 256 megs of video ram.  the proprietary drivers afford me excellent 3D acceleration.  the cavat is i am good until they discontinue support(the proprietary is shit-reality).

as to azz's question.  open source 3D acceleration is pretty lacking with newer hardware.  you can, checkout the DRI project: [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/) for support for older cards.  i have not heard that the DRI drivers are that buggy.  i have heard stories of people playing enemy territory with acceptable framerates in gnu/linux.

basically ATI opened up specifications for thier older hardware, DRI came to the rescue to provide free 3D acceleration built into x and the kernel.  nvidia provides a 2D opensource driver as does ATI on newer cards.  however, nvidia has never released a open spec for a card and ATI has failed to do so for thier newer ones.

so basically if you want open source 3D you are stuck with older ATI cards supported by the  [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/) (they have a list) OR going with a vendor that provides them.  personally, i would purchase an older ATI card.

i hope someday vendors become more sane and open up thier specs or better yet the drivers.  however not all 3D code in the proprietary driver is property of nvidia or ATI.  anyways, 3D opensource video has aways to go.

btw, check out planet penguin racer: [http://projects.planetpenguin.de/racer/](http://projects.planetpenguin.de/racer/) 
basically, tuxracer has been abandoned and this project has more updates maps and the game features.  

if you want to run tuxkart, check out supertuxkart.  tuxkart is a great game, however supertuxkart adds new models, tracks and gameplay.

also a very well done 3D game is neverball.  it is very challenging and fun to play.

i hope that helps azz.

---

### Post by az on 2005-04-26
Thank you!  That is bang on what I wanted to know.

---

