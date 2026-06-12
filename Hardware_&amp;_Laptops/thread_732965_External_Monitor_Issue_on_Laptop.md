---
title: "External Monitor Issue on Laptop"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by Ryupower on 2008-03-23
First of all: hi.
I read many other discussions and googled all around the world wide web, but the problem still won't resolve.

I have a laptop ( ATI Radeon Video Card ) and just bought a brand new monitor, which has a  higher resolution ( LG Flatron W2252RQ ).

Ubuntu simply won't recognize it. I mean, it sends video data over to it, but the laptop won't shut its own monitor down, nor does it even notice that there's an external monitor. 

I've tried turning off special effects, doing *Sudo dpkg-reconfigure xserver xorg*, System>Admin>Screens and Graphics ( where it claims there is no second monitor ), and many other things. But I still can't get the resolution up to 1680 X 1080! The Ubuntu screen just stays in the upper left corner, penals and all.

I looked all over for a driver for this monitor, but I couldn't find it. 

Can anybody help me please?

P.S.: My card supports it, because it works on windows.

---

### Post by Ryupower on 2008-03-23
Okay, I got rid of the upper-left corner thing after killing Gutsy, and reinstalling Feisty.  I don't know if it'll do the resolution thing, but at least it's taking up the whole screen.

It appears to be a bug in Gutsy that needs some fixing. *had to format the partition and install Feisty* :(

---

