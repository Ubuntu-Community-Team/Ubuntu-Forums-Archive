---
title: "Installing with 80mb of RAM"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by intrepid4968 on 2007-07-05
According to help.ubuntu.com, Ubuntu is supposed to be able to be installed via the text installer on systems with at least 32mb of RAM. Well, I have tried to install it on a system with 80mb of RAM, and it doesn't work, so here I am.

The computer is an ancient Hitachi Visionbook 4000 (Pentium 150Mhz, 80mb) which I am trying to turn into a digital picture frame. It currently has an install of Suse 8.2 on it, which was on it when I dug it out of the basement. Suse 8.2 is useless because I can't get anything to be compatible with it cause it's so old, so I thought I'd try a command line install of Ubuntu.

The (text mode) installer gets almost all the way through the hardware detection and driver loading stage and then goes to a black screen with the word 'Killed' appearing on the left side of the screen. I am completely baffled, but I figure someone with more Ubuntu skills than me might know the answer.

---

### Post by tgalati4 on 2007-07-05
Sometimes hitting esc or Control-C during the boot script will dump you out before the error.  Try booting and watch exactly where it dumps.  Then reboot and Control-C just before the hang.

That way you can get to a command line and start to look at /var/log for interesting messages.

With limited RAM, I would look at Damn Small Linux.

If you are experiencing a hardware detection problem, then try a later version of SUSE.  There's probably a text installer for it somewhere.

---

### Post by intrepid4968 on 2007-07-06
I just went with DSL. Thanks for the help.

---

