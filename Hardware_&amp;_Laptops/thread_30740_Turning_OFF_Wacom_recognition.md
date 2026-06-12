---
title: "Turning OFF Wacom recognition"
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by cyli on 2005-04-30
I did manage to get my USB Wacom Intuos tablet working under Ubuntu, although sometimes the events change for some reason.

My main problem is that I would like to use OpenCanvas (graphic program) under VMWare, and I can't get VMWare to list the tablet under it's USB devices.

[This](http://www.linuxjournal.com/node/6103/print) is an old article about Dreamworks using VMWare on a Linux host, and they mentioned that to get their tablets working they had to turn "off" the tablet in X.  Otherwise, if I just use the tablet there is no pressure sensitivity - the tablet works just like a mouse.  I know that VMWare in a sense unplugs the USB device from the host system in order to get it to work on the guest system.

I've commented out all the tablet-related info in xorg.conf, and I've also rmmod-ed wacom, but VMWare still doesn't list the tablet in its list of USB devices.  I'm not sure what else to do.

I apologize if this is the wrong forum to ask, but so far I've only found information about getting the tablet to work and not the reverse.  Thanks in advance for any advice anyone can offer. 

*Note* - ideally, this process would be easily reversible, as I would like to still be able to use my tablet with Gimp too.

---

