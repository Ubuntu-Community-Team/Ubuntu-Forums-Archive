---
title: "ATI Rage 128 Pro gives no output on screen"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by bjholmem on 2005-05-24
I have installed Ubuntu Hoary Hedgehog on my desktop computer. It's got an AMD Athlon 2500+ processor and 512 MB of RAM on an MSI KM4M mainboard. The integrated video adapter is disabled by and AGP ATI Rage 128 Pro card w/ 16 MB video RAM.

My problem is that when I boot with Ubuntu, and I get to the login screen, the monitor only displays a black screen. I can log in, but I don't see anything. I have fiddled around with the dpkg-configure xserver-xorg, and depending on what I do, when I boot up I either get an error message that X can't be started (because of no screen found, when I read the dmesg) or the monitor just goes black and displays that the sync rate(s) is too low (typically around 40 Hz vertical sync). 

I have tried googling for solutions to this problem, and the closest I got was in the ubuntu wiki to install the fglrx-driver, but that wouldn't happen as it was conflicting with another driver. I would have included all the error messages and dmesg-files here, but I can't see anything after I boot other than in a text based mode, and that makes it difficult for me to post them since I am doing this from that other OS :( (I'm a linux n00b :-/ ) 

Any suggestions would be appreciated, preferably in a how-to format :)

Yours, 
Bjornar

---

