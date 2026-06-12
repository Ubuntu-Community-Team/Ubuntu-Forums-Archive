---
title: "Ubuntu doesnt detect my soundcard!"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by Kanephan on 2005-11-24
And I have no idea what to do :( 

I think its a Rockwell. I'm not sure how to check if it isnt detected.

Please please please help me get this thing working.

---

### Post by Kanephan on 2005-11-24
A lot of people on the board are complaining about sound problems, but for all I've seen, their card is detected. Mine isn't at all...

What the hell then? I'm losing hope :(

And I just realized I should've put this in the Video/Sound board. Sorry about that.

---

### Post by Kanephan on 2005-11-24
This looks like my problem:

[http://www.mepis.org/node/6848](http://www.mepis.org/node/6848)

I probably have a Rockwell RipTide, as the computer is an older HP just like they say.

---

### Post by az on 2005-11-24
For most older (isa) soundcards, the kernel cannot probe them safely so that is why they are not detected.  You can load the drivers yourself like this:

[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

As for the riptide modem, linuxant provides 2.4 kernel drivers.  The people at rockwell/Conexant did not release the specs to the dhipset AFAIK and that is why there are no non-proprietary up-to-date linux driver for them.

Sorry.  This probably merits a complaint to Conexant (Rockwell)

---

### Post by Kanephan on 2005-11-24
Uh oh. I installed an older version of dpkg over the one I had, and now I can't install anything. The terminal keeps giving me this error:

dpkg: configuration error: unknown option log: Success

I tried reinstalling dpkg, but they give you a .deb file to install it! So its a catch-22 so to speak...

---

