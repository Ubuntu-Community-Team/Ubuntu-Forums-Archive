---
title: "HP 1280 deskjet will not print to A3 using HPLIP"
date: 2016-02-11
forum: Hardware
---

### Post by Deanobats on 2016-02-11
Hi all,
I have an interesting problem (well, irritating as well as interesting). I'm on Ubuntu 14.04 LTS 64 bit using HPLIP-3.14.3 to print to a HP 1280 deskjet via usb. It's the only A3 printer I have, and while I don't use it very often, it's useful for printing out the odd map. A4 is fine, we like A4, A4 works. However, when I try to print up to A3, from a whole range of applications, Inkscape, gimp, libreoffice etc etc, it no worky.

The application recognises that it's A3, all the paper settings in a whole range of places are set to A3, but what comes out is an A3 piece of paper scaled to fit A3, but with only the top left hand corner printed as though through an A4 window. In other words, I get an A4 sized cropped section of an A3 print. 

Now my suspicion is that somewhere, the margins are still set to an A4 size, meaning that the image will not fill the whole paper. This grand theory of mine would only work however if margins are all set from the top and left hand margins, so that the right hand margin was set as a certain distance from the left hand of the paper. If the right margin is set from the right hand side of the paper, then I am clearly barking up the wrong tree. Any suggestions?

I have temporarily worked around this problem by exporting the image to a windows-compatible format to a shared directory with a Windows XP Virtual Machine and printing it from there. Not exactly ideal.

Ta!

---

### Post by Deanobats on 2016-02-16
I found a possible solution that someone has posted (to one of my requests in fact!) that "Installing printer-driver-hpijs and choosing that driver from printer settings" would work, but I have no idea how to do that! I think hpijs is a more limited driver that than the default hplip driver but I get very confused when trying to understand printer drivers under Linux.
Can anyone educate me?
Ta!

---

### Post by Deanobats on 2016-02-17
Ok, so here is what I did in case anyone has the same issues.

I know that the 1220C printer driver will work (partly) with the 1280 as there is no windows 7 driver for the 1280 so it's recommended that you use the 1220C driver instead. So within system settings printers, I created a duplicate of my 1280 printer that I could play with. Within properties I changed the Make and Model to a 1220. Firstly I used the 1220C hpcups 3.14.3 driver, no luck there, still same problem not printing to A3. Then I tried the 1220C Foomatic/pjxl300 driver, again, same problem. Then I tried the CUPS+Gutenprint v5.2.10-pre2 driver and BINGO! Prints to A3. Now I don't think that the 1280 is supported by Gutenprint, but the 1220C is. I don;t have as many options in terms of print quality as I would using HPLIP, but at least it prints to A3 now.

---

