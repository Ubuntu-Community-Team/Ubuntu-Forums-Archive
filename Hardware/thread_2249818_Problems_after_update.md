---
title: "Problems after update"
date: 2014-10-24
forum: Hardware
---

### Post by wolfen10862 on 2014-10-24
This morning before I went to work I was trying to email something and Ubuntu 14.10 gave me a box that said theres an upgrade available, so I clicked accept, Now I can't use my video card, the card is a Nvidia 8400GS I need this card working so I can use the computer, the stock mother board drivers aren't worth a darn, and I have no idea how to use a terminal to even look for them let alone install them

---

### Post by weatherman2 on 2014-10-24
Restart the computer and hold down the Shift key.  You should get a Grub boot menu.  From this, choose "previous versions" and choose the kernel at the top of the list (hit Enter) and see if that boots up and works.

---

### Post by grahammechanical on 2014-10-24
Or, at the Grub boot menu open the Advanced Options for Ubuntu sub-menu and select Recovery mode. At the recovery menu select Resume. That may get you to a desktop using an open source video driver and from there you can use System Settings>Software and Updates>Additional Drivers tab to experiment with video drivers.

What do you mean by "cannot use my video card?" Please explain. Otherwise, we may be giving advice that is not applicable to the actual problem.

The latest version of Ubuntu always has the latest stable proprietary video drivers. Often companies like Nvidia remove support of older video cards from their latest drivers. Has this happened to you? The software centre may have an older Nvidia driver that may support your card. Or you can use Nouveau the open source video driver that is in Ubuntu as a default video driver. I am using it on my Nvidia GT220 even though Nvidia still supports my card.

Regards.

---

### Post by wolfen10862 on 2014-10-24
Thanks for eth replays guys when I say I cant use teh video card I mean if I install it in the computer with or without a cable plugged in teh monitor does not come on, all I get is the orange light that tells me theres no signal, if I remove the video card the video works if I plug the monitor cable into the mother board graphice port.
I need this fixed becaus eI have o have a video card for something and I'd really really hate to go back to windoes cause Vista crashes more than I change pants

---

### Post by wolfen10862 on 2014-10-25
I'm still having problems, with the upgrade theres no grub menue on shift, don't know if I got a bad download or what, but I'm trying to reinstall 14.04. If that doesn't work I'm screwed, but so far the video card seems to be working with the install

---

### Post by wolfen10862 on 2014-10-25
Ladies and gentlemen. We can consider my problem solved. Here's what I did, I turned off the computer, looked at my windows disk and shuttered, reinstalled the video card and cable, booted Ubuntu 14.04.1 and I think I missed up on the first install. Because I left the disk in this time until a notice to remove it ant press enter showed up, which I didn't do last timthe
Please forgive any spelling errors, I'm posting this from my phone as Ubuntu still needs a couple of downloads before I start using it and this site usxtunnjng slow as hell on my phonr

---

