---
title: "I want to disable my default soundcard (1 out of2)"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by cowlip on 2005-08-04
Hi,

I have an onboard soundcard that doesn't work, as well as a Soundblaster live.  I can choose all this in Beep media player and Audacity, but WINE programs don't let u choose, so I have to have soundblaster as card 1.

So, How do I get /dev/dsp1 to function as the soundblaster instead of my onboard card?

---

### Post by kleeman on 2005-08-04
I have done this in the past by using a .asoundrc file. Here is some info to start with:

[http://alsa.opensrc.org/index.php?page=MultipleCards](http://alsa.opensrc.org/index.php?page=MultipleCards)

Check out the Debian specific info and the .asoundrc info
Good Luck!

---

### Post by cowlip on 2005-08-04
[QUOTE=kleeman]I have done this in the past by using a .asoundrc file. Here is some info to start with:

[http://alsa.opensrc.org/index.php?page=MultipleCards](http://alsa.opensrc.org/index.php?page=MultipleCards)

Check out the Debian specific info and the .asoundrc info
Good Luck![/QUOTE]
 Thx a lot this looks helpful

---

