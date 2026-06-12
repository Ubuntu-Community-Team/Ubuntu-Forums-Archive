---
title: "Soundblaster Awe64 Gold not working"
date: 2008-10-11
forum: Hardware
---

### Post by coreychch on 2008-10-11
Hey all... First time Linux user, and I have installed Ubuntu 7.10 onto a computer that was using windows. The Soundblaster Awe64 Gold soundcard isn't being detected (though it worked well on windows). Its a Dell P3 500mhz.  The lspci command in terminal detects no multimedia devices at all. 

I have read around lots, trying to solve this problem.  My reasonably technical brain with no Linux experience is getting tired of trying things out and reading copious amounts of material trying to comprehend what my problem could be.  I even tried another Linux 'dynebolic' and had a similar problem... though dynebolic detected the soundcard, it wouldn't work.

I have tried the ALSA page and came up with 
[http://www.alsa-project.org/main/index.php/Matrix:Module-sbawe](http://www.alsa-project.org/main/index.php/Matrix:Module-sbawe) 
Apparently the right driver, though its a bit difficult to follow. I'm pretty sure I have added the driver following these intstructions using the sudo-e command in terminal. But still no dice!  Feels like I'm a bit lost here, and the street signs are in another language... help?  

Thanks, really appreciate any useful input. (This is a bummer as I intended to use the computer for music.)

---

### Post by kostkon on 2008-10-11
> **coreychch said:**
> Hey all... First time Linux user, and I have installed Ubuntu 7.10 onto a computer that was using windows. The Soundblaster Awe64 Gold soundcard isn't being detected (though it worked well on windows). Its a Dell P3 500mhz.  The lspci command in terminal detects no multimedia devices at all. 

I have read around lots, trying to solve this problem.  My reasonably technical brain with no Linux experience is getting tired of trying things out and reading copious amounts of material trying to comprehend what my problem could be.  I even tried another Linux 'dynebolic' and had a similar problem... though dynebolic detected the soundcard, it wouldn't work.

I have tried the ALSA page and came up with 
[http://www.alsa-project.org/main/index.php/Matrix:Module-sbawe](http://www.alsa-project.org/main/index.php/Matrix:Module-sbawe) 
Apparently the right driver, though its a bit difficult to follow. I'm pretty sure I have added the driver following these intstructions using the sudo-e command in terminal. But still no dice!  Feels like I'm a bit lost here, and the street signs are in another language... help?  

Thanks, really appreciate any useful input. (This is a bummer as I intended to use the computer for music.)
Are you sure that you have the *PCI* version of this card and not the *ISA* one?

If it is an *ISA* card, then obviously *lspci* will not output anything. Also, *ISA* devices are not recognised automatically anymore (it's an obsolete technology) so you'll have to load the driver yourself.

Please, check [this page]("https://help.ubuntu.com/community/HowToSetupSoundCards") from the *Ubuntu* documentation site for instructions on how to do it.

If you have indeed an *ISA* card, then I believe you'll need to load the *snd-sbawe* driver.

---

### Post by coreychch on 2008-10-11
YES!
Thanks for that very helpful link Kostkon, I managed to nut it out and now have sound for the first time!  It seems to think my card is a different model, the soundblaster 16 but at least it works!  Maybe I'll look into this further if it plays up but for now I'm happy!  Must have been ISA after all?  Thanks again...very much! Corey

---

### Post by kostkon on 2008-10-14
> **coreychch said:**
> YES!
Thanks for that very helpful link Kostkon, I managed to nut it out and now have sound for the first time!  It seems to think my card is a different model, the soundblaster 16 but at least it works!  Maybe I'll look into this further if it plays up but for now I'm happy!  Must have been ISA after all?  Thanks again...very much! Corey
If it's working just fine, great! :)

And, since you are a new user, I would like to welcome you to the Ubuntu community!

---

### Post by coreychch on 2008-10-15
Thankyou, I appreciate the welcome

---

