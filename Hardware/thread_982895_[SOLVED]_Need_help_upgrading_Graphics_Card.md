---
title: "[SOLVED] Need help upgrading Graphics Card"
date: 2008-11-15
forum: Hardware
---

### Post by lrs52200 on 2008-11-15
My son has a Dell Optiplex 150, Model DHM.  He's running Ubuntu 8.04 LTS

The computer came with what appears to be a K-Mart Blue Light Special Graphics Card.  It's AGP.
I found an ATI Xpert 128 (PCI) Rage card laying around the house and want to swap them out.  However, it does not appear to be as simple as removing the AGP and replacing it with the PCI because when I tried that and rebooted, I only got as far as the Ubuntu loading screen, then everything went black.  I'm guessing this is because I did not remove the old drivers first.
I need someone to give me a step by step tutorial here.  Where do I find the old drivers so that I can remove them?  And what do I do next?

Thanks guys.......
:)

---

### Post by ssam on 2008-11-15
try:
shutdown
put in the new card
at the grub screen (this is the bit when booting that lets you choose between ubuntu, windows and old kernels) choose the ubuntu recover option.
select the fix X option.

---

### Post by lrs52200 on 2008-11-15
ssam-

  Thanks for getting back so quickly.  I was able to follow all of your instructions and the computer booted.  When I tried to enable extra visual effects, It didn't work.  It remains on 'none.'
  I tried to update, thinking it would install the proprietary drivers, but discovered that they were already installed.  I looked at the screen savers to see if there was any improvement there because they used to lurch (you know, kind of move, then stop, the continue moving, etc).  There was no improvement there either.
  I then put in the CD that came with the card but was unable to get anything to happen.  The files wouldn't open.
  Do you have any clue as to what the problem is?  According to the box, his computer should be able to use this graphics card.

Thanks again-

---

### Post by Skripka on 2008-11-15
Odds, are it is because your card is not supported under Xorg 7.0 and above (the card in question is almost 10 years old).


[http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html](http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html)

Nor is it supported by the fglrx drivers in the *buntu repos., t'would seem....

[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

---

### Post by lrs52200 on 2008-11-15
Thank you for the info.  I didn't realize the card was that old.  Okay, I guess I'm off to the store for a better, newer card.  :)

---

