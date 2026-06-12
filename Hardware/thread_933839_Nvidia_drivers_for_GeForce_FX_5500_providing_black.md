---
title: "Nvidia drivers for GeForce FX 5500 providing black screen"
date: 2008-09-29
forum: Hardware
---

### Post by TheIdiotThatIsMe on 2008-09-29
Howdy!

I have tried a few different ways to install the NVidia driver (including through the restricted drivers and also the Envy package) and for some reason, each time I boot after installing an Nvidia driver, it shows the booting progress bar, then goes black and stays there until I manually power off the computer. I am able to go back to the desktop after booting into recovery and running the xfix option, but then am left without using the driver. I am currently running an Nvidia GeForce FX 5500 AGP.

---

### Post by AnonCat on 2008-09-30
You might need to blacklist your onboard video device even if it's disabled.  I had the same problem and that was the only way I could get the nvidia card to work which is also a 5500 FX.

---

### Post by TheIdiotThatIsMe on 2008-09-30
How do I "blacklist" the onboard device? I also went into the BIOS to see if there was an option for disabling it, but couldn't find an option for it (the desktop i a Dell Dimension 4600).

---

### Post by TheIdiotThatIsMe on 2008-10-01
Okay, tried the blacklisting, but didn't work.

I've tried the regular ubuntu-restricted-drivers, Envy, and two drivers from the site. Unfortunately none of them worked :-( All of them provided a blank screen excpet the 7667 driver because it couldn't compile I guess on Hardy.

---

