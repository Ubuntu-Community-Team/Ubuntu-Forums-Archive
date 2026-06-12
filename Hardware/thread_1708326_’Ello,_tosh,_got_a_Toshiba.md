---
title: "’Ello, tosh, got a Toshiba?"
date: 2011-03-16
forum: Hardware
---

### Post by ubunwho on 2011-03-16
OK, so i made the leap. I am not a "computer person" but the website made it all sound so easy and great...

Help.

All I have is a laptop with a black screen...

So far I have done a wubi install of 10.10, which worked but crashed a lot.
Tried to update some stuff but did not have space on the "/" drive.
Installed LVPM to change the size of the root drive. The first time i started the computer after LVPM install I was given an option (in DOS?) to start LVPM, I tried but got an error message, (sorry I dont know what it was). Had to do Ctrl, Alt, Del to restart.
After restart computer does nothing, screen has not turned on, HD does spin up but does little, if any reading, cd/dvd drive will start if there is a disc in it but it will not boot from a live cd I made of 10.10 on my mac.

Toshiba Satellite A100 523, Celeron M, ATI graphics

---

### Post by ieee488 on 2011-03-18
I don't know what LVPM is.
I have never had to do anything with that when installing Ubuntu to my Dell laptops.

Are you able to run the Live CD?

---

### Post by ubunwho on 2011-03-23
I have managed to get the live cd working by running in "nomodeset"

My problem still persists after I install.

I have to edit the boot file. (press e in grub2 menu) Then find "quiet splash" and replace with "nomodeset". Hit Ctrl-X and it will run normally.

Is it because there are no drivers for my ATI card?

I have used the terminal to edit my grub file permanently so that it boots in nomodeset every time i start up. 

What am I loosing by being in nomodeset?

---

