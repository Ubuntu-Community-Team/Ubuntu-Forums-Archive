---
title: "Dell Optiplex GX1 Pentium 2"
date: 2008-07-09
forum: Hardware
---

### Post by deucalion on 2008-07-09
I know this Dell Optiplex GX1 i am setting up for a couple who want an "Internet/E-mail/Shopping" PC. Okay, so it sucks and they want something cheap. I'm recycling. (I work at a computer repair store). So i am unable to get the audio card to work. Not a clue what it is. Stock card. Did a google search and got nothing. Any help on configuring this would be great. And for some reason, when i plug headphones in them and force a system beep (user$desktop: in terminal and then hit backspace a ********) it beeps via headphones, not the system speaker. 

Thanks for any help! Pat

---

### Post by him610 on 2008-07-09
I also have a GX1 P2 loaded with Xubuntu 8.04, and was able to get everything to work. It's a good sturdy machine, fairly easy to setup and configure.

I'm sorry that I can't give you anything more than encouragement because I getting ready to go on vacation and don't have a whole lot of time right now.

Cheers!

---

### Post by him610 on 2008-07-09
I checked the specs of the onboard audio chip for the Optiplex GX1, it is listed in the online Dell documentation as a Crystal Semiconductor CS4236. Ubuntu is pretty good about configuring itself for legacy devices.

The builtin speaker is only for diagnostics, system beeps, etc. Do you get one short beep when you boot up?

If there is an audio card installed in one of the ISA or PCI slots, you can probably determine what it is by typing "lspci" from the CLI in a terminal.

Good luck.

---

### Post by sTpny on 2008-07-31
Hi,

It wont work.. auto detection of that card was disabled because it was causing hangups in some configurations.  you must set it up manually.. luckily.. this is easy....

this keyboard is broken--- so theses are slashes... < ok,,,

open your modules file as root.  this has things that must load, but are not included in the kernel.

sudo gedit <etc<modules


add the line....

snd-cs4236

save and close...

open your system preferences sound 

uncheck enable software sound mixing..

reboot.

My sound comes out of the audio out on this gx1 instead of the speaker out port, but it still has sounds..  3d graphics are possible too.. good luck.

---

