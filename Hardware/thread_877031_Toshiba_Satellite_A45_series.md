---
title: "Toshiba Satellite A45 series"
date: 2008-08-01
forum: Hardware
---

### Post by ginbas on 2008-08-01
This is not a DIY guide but more so just a reference of speed bumps and hurdles for anyone who wishes to run "hardy 8.04" or possibly other versions of ubuntu on the a45 series laptops. 

First, note that for whatever reason the live cd has a problem and hangs on setting up gnome. As a work around I used the text based install and it worked without issue.

Second, the intel 852GM graphics works with acceleration out of the box and desktop effects are enabled by default. However, I would recommend turning them off because the performance is not quite up to par especially scrolling with firefox.

Third, drive performance is terrible. The newer versions of ubuntu automatically set the drives up under /sda to emulate and to create compadibility with serial ATA drives (to the best of my knowledge). What I did to work around this is to convert to /hda and then recompile the kernel to enable the piixn ide driver. This after hours and hours of googling was able to get ultra dma working in 32 bit mode. 

Forth, note if you compile the kernel and choose to copy all existing settings, for some reason is doesn't include the audio driver. So make you when you enable the "piixn driver" you also enable the audio driver "ac 97" if I recall. 

You should then have a good working system. I also have some issues with the location of firmware drivers after the kernel compile but that was specific to a usb wireless device. My unit does not have built in wireless adaptor.

Hope this sort of helps.

---

