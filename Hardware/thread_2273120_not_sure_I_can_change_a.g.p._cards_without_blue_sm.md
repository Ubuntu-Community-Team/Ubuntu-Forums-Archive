---
title: "not sure I can change a.g.p. cards without blue smoke"
date: 2015-04-10
forum: Hardware
---

### Post by Ka Fish on 2015-04-10
I have this AOpen S760GXm-US motherboard with a Geforce 6200 256k agp card in it now. The video is draging. I want to see if replacing it with a Radeon 9500 128m agp card would be an improvement. There is a plug on the side of it that fits the floppy drives power suply. My first question would be is can I plug it in without burning out my motherboard? Should I install any drivers before swapping the cards?

---

### Post by grahammechanical on 2015-04-10
The only advice that I can give is in regard to the drivers. Before you change video adapters switch to the open source video drivers. Your present card is Nvidia. The replacement is AMD/ATI. They do not use the same proprietary driver.

So, if you change video adapters and then restart you will have problems because the ATI card cannot use the Nvidia driver but it can use the open source driver. Once the change has been made and you have restarted to a working desktop, you can then use Additional Drivers to set a proprietary video driver.

I am assuming that you are using a supported version of Ubuntu and not an out of support version. Otherwise you will not be able to install the AMD driver because the software repositories of out of support versions are closed.

Regards.

---

### Post by Ka Fish on 2015-04-11
I have changed video cards. The blue  port is working but the digital one is not. The softwhere center said E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E:  Unable to correct dependencies. I tried to use synaptic package maniger  uninstall the drivers I don't need & install the ones i need. It  told me Could not apply changes!
Fix broken packages first. How do I find & fix held broken packages?

---

### Post by Vladlenin5000 on 2015-04-12
Youbshouldn't have to go about it manually, with Synaptic or any other tool... And the previous post says *IF* you had proprietary nividia drivers in use *THEN* you must uninstall (actually purge) them before swapping to an ATI/AMD or other, because otherwise you'll have some not-so-easy-solvable problems. 

Now, if you had the open source driver for nvidia you don't even need that, simply take one out and put the other in. If proprietary AMD drivers are required then you need to install them, just like you would anyway.

The broken packages you have now may or may not be related to what you did (uninstalled or tried to) before with Synaptic (it probably IS related). If I remember correctly Synaptic has a function for that, check the menus. Otherwise:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
sudo apt-get remove --purge nvidia*  (just in case...)

```

---

### Post by Vladlenin5000 on 2015-04-12
The good/bad news is that the newest AGP card with ATI chips you can find is already legacy, according to AMD. As such, they no longer provide Linux drivers for that card. Good or bad, the open souce driver, the Ubuntu default, is the one you'll ever use.

---

### Post by user_of_gnomes on 2015-04-12
> There is a plug on the side of it that fits the floppy drives power suply. My first question would be is can I plug it in without burning out my motherboard?

There's a good chance the videocard won't work without it. [Judging from the manual ]("http://www2.ati.com/manuals/Getting_Started.pdf") it should have come with a power cord, do you still have it?
I guess that if you no longer have it you could substitute it with a diskette drive power connector but since there is no pin-out in the manual I can't tell for sure. Judging from the pictures on the web I'd say it's a fit.

---

### Post by Ka Fish on 2015-04-13
Everything went well in the terminal until that last line. I got Command line option 'p' [from -purge] is not known. I used synaptic package manager to to remove everything I could find that to do with Nvidia. I forgot it told me I couldn't uninstall something in use when I still had the Nvidia card in. I salvaged the Radon card & didn't relies I needed to take the cord too.

---

### Post by user_of_gnomes on 2015-04-14
You can work your way around requiring the extension cord, no doubt. Most likely by indeed hooking it directly up to the diskette power supply connector. Just confirm that this is possible by doing some research first.

I think it should be apt-get purge and not apt-get remove -purge, by the way.

Edit: apparently remove --purge will also work.

---

### Post by Vladlenin5000 on 2015-04-14
Yes, thanks, edited and corrected. Thta's what happens when using a tablet with touchscreen only... :(

---

