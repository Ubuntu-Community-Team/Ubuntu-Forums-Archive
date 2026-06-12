---
title: "2 Problems (internet and XFree86)"
date: 2005-01-16
forum: Installation &amp; Upgrades
---

### Post by MrTrumpets on 2005-01-16
First off, I'm a 99% Linux Noob.  My network connection is on the motherboard.  I don't know if this matters or not.

On my PC, I took the plunge. (sp?)  I formatted the PC.  I usually use Wireless (WinXP), so I was prepared for no "inital" wireless connection.  I simply enabled the on-board CAT5 connection in the bios, and used my laptop wireless WinXP connection to SHARE that internet connection on my desktop.

I installed Ubuntu on a VMWare (5.0 beta.. very nice) and it was 100% perfect!  I was even able to install those "tricky" VMWare Tools.

During the VMWare install it noticed that it grabbed the DHCP internet connection and updated before completing the install.

I THOUGHT it would do the same because of my laptop sharing the connection.
It didn't.  To test to make sure I setup Windows Internet connection sharing up correctly, I rebooted, and popped in my Knoppix CD.. it grabbed an IP Address and got online in only seconds.

I decided to try to reinstall Ubuntu..
The exact same results happened.  It also couldn't "startx" (XFree86).  It said I need to configure.

I'm so confused, but ever since I saw that I can play World of Warcraft on this using another program, I'm ready to change forever.. I only use Windows to play games and all my games now work on Ubuntu!

please help a noob.

-Frank  :confused: (currently on the laptop.. not able to play games lol)

---

### Post by MrTrumpets on 2005-01-16
Same problems.. Here's the XFree86.0.log from the hard drive. (Currently online with the PC using a Knoppix CD)

--------------------- begin log ----------------------------

EDIT.. removed log..

---

### Post by Rancoras on 2005-01-16
Your post isn't very clear so I'm just guessing here.  You say you installed ubuntu into a VMWare virtual machine.  That was before you formatted the machine, correct?  You say that install went well and the network connection was working correctly.  You then formatted the machine and installed ubuntu "for real" and the network connection didn't work?  This may be because the virtual network card in VMWare and the real network card in your PC are different.  What network card is in the PC?  I know you say it's on the motherboard, but that doesn't say much.  Let's solve this problem before worrying about why X isn't working.

P.S. Please use code tags when posting logs and terminal output.  It makes it much easier to read.

---

### Post by MrTrumpets on 2005-01-16
I cannot find that info.  Should I disable the on-board lan and slap one of my linksys 10/100 pci cards in?

---

### Post by MrTrumpets on 2005-01-16
Well, I put in a Linksys card and I got online.. I downloaded all patches with a "REAL" install.

Now I just need to configure the XFree86 thing..

I'll go search.. again.. I just don't understand how to do that. 

I use GeForceFX 5600 256MB on AGP 8x.  Maybe that helps.. maybe not.

---

### Post by Rancoras on 2005-01-16
I'm glad your network is working now.

The VMWare virtual video is different than the 5600.  That's the problem with using VMWare as a preview medium.  It's a virtual machine and the "hardware" isn't necessarily what you have in your "real" machine.


I can't remember if there are any issues with the 5600 or not.  I think this issue is that same as the network card.  You could try installing the nvidia drivers with the information on [www.ubuntuguide.org](www.ubuntuguide.org) .  Post back if you have any problems with the instructions there.

---

### Post by MrTrumpets on 2005-01-16
I'll do my best.  My biggest problem NOW is trying to "configure" XFree86.  I have been browsing the web for hours.. I don't get any of it.  I found 1 command called "xf86config" and after the entire setup it said I couldn't create a XF86config because I was not root.

I'll check out the site.  Thanks for the help so far!

---

### Post by MrTrumpets on 2005-01-17
Thanks for the help. :)

I'm using Ubuntu to type this.   :D 

Woohoo!  Now if I could only get all 3 mouse buttons to work.. I'll post that in another place, since this is an installation forum.  

Thanks again!

-Frank


btw.. manually configuring the XF86Config-4 file sucks!  lol

---

