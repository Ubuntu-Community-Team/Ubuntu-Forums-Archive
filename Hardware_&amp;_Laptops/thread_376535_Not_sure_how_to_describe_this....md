---
title: "Not sure how to describe this..."
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by JoeF_3 on 2007-03-05
So, I have a bit of a situation.

About 2 years ago I purchased a Toshiba m200 TabletPC.  I love it. But some time after the warranty expired (it was a refurbished laptop, so had only a 1 year warranty instead of the 3 year that came standard with the non-refurbished version), the hard drive failed, quite spectacularly.  It now is completely unreadable, even as a slave drive in my main PC.

The tablet is a secondary PC (and always has been), and I'd been thinking about going to Linux for some time now with a secondary PC.  And now I need to make the laptop work on a new drive, and I've seen reviews suggesting that Linux on a tablet is a quite nice experience, so I've been considering giving it a try.

Herein lies the problem.  The m200 has no optical drive, and will not boot from USB (apparently there is a bios upgrade that will fix this).  It will boot from an SD memory card, but I don't currently own one, and my main PC has no card reader.

I purchased a new hard drive, and installed Ubuntu on to the new hard drive by installing the hard drive in my primary computer and running the install cd from there.  This worked perfectly.

I installed the hard drive onto my laptop, and got an error message saying that Ubuntu could not load it's GUI, and then got sent back to the command line.  It appears that the OS boots fine, but is expecting my desktop's hardware, which is nothing like the laptop (Desktop is an 64 bit single core Athlon with an ATI video card, tablet is a Centrino platform with a GeForce Go).  

I have no idea how to do anything from Linux in the command line, and am not very good at figuring it out.  Give me a GUI, and I'll be able to play around and intuit my way into solving most problems (plus most instructions on how to make various tablet features work that I've found reference the GUI, not the command line).

So, intrepid Ubuntu community, how do I install Ubuntu on to a drive in one PC with the intention of it booting successfully to a GUI desktop in a second, very different PC?  Or Alternatively, what do I have to do from the command line to get back into a GUI so that I might make the laptop work the way I want it to?

---

### Post by rumblered on 2007-03-05
Ubuntu sets up the driver for your video card at install time.  To reconfigure the system, log into the text console with your username and password, then run 'sudo dpkg-reconfigure xserver-xorg' to update your video configuration.

Then you can bring the GUI back up with 'sudo /etc/init.d/gdm restart'.

---

### Post by JoeF_3 on 2007-03-05
Thanks!  It took a few tries to get the configuration to work, but I finally got Gnome to load.  Now to get all of the various tablet things and whatnot working...

---

