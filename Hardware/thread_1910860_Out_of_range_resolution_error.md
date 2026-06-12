---
title: "Out of range resolution error"
date: 2012-01-17
forum: Hardware
---

### Post by Creddeus on 2012-01-17
Hey, guys. I just upgraded to Oneiric and it's giving me some resolution problems. I had the same thing with Natty Narwhal and had a friend fix it but figured I'd see if I could do it myself this time. The thing is that, when I start up Ubuntu, my monitor says the frequency is out of range or something. Only in the boot loader, though. If I wait long enough it will load the default setting and it's pretty much smooth sailing from there. With the exception of a few graphic glitches here and there. I'm not sure if that's Oneiric or not.

My friend said the problem it was having before was that my monitor was telling Ubuntu that it has more capability than what it can actually handle so he had to set it to to a specific res using the terminal. Unfortunately, I'm too new to Linux based operation systems to effectively use the terminal.

I'm using NVIDIA GeForce 6150SE nForce 430. My resolution should be set to 1280 x 1024.

Any suggestions?

---

### Post by grahammechanical on 2012-01-17
Do you have the Nvidia proprietary video driver activated through Additional Drivers? If so then it will put a Nvidia X-Server Settings Utility that may let you adjust the video resolution. Just type Nvidia in the Dash.

Regards.

P.S. There is something else that I have just thought of. If this problem is happening when the boot loader (Grub) loads then you might try installing something called Grub Customizer. It has an appearance tab that lets you set the resolution. That just might allow you to set Grub to run at the correct screen resolution without needing to manually edit the Grub configuration files.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by saneearth on 2012-01-17
Sounds as if the grub splash screen resolution is out of range. You should be able to use start up manager and adjust the resolution of the boot screen. This will enable you to "get back in range". From what you have said the resolution issue or out of range issue is with the boot splash. There are other tools to set the resolution in the boot splash and it can be done in the grub config itself, but I am not sure where. Lots of changes over the last couple of years or so with grub.

---

### Post by Creddeus on 2012-01-18
I don't seem to have any application called "startup manager" installed so I'm going with the grub customizer. I have a question, though.

In the grub customizer settings, I can change the screen resolution but it has options for 1280 x 1024 x 8, 1280 x 1024 x 18, and 1280 x 1024 x 24. Does it matter which one I choose? I've never run across options with three dimensions.

Thanks.

---

### Post by Creddeus on 2012-01-18
Oh, and yeah. I have the proprietary drivers. Will that effect the boot loader, though? I didn't think those settings would be loaded until Ubuntu boots up. NVIDIA X Server Settings are set as a startup program.

---

