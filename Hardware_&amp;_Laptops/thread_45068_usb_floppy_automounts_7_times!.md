---
title: "usb floppy automounts 7 times!"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by awry on 2005-06-28
I'm a seasoned gentoo user, but relatively new to ubuntu (much nicer for my thinkpad).  I have a weird problem.  When I plug in a usb floppy drive (an unfortunate necessity), it is autodetected, and then mounted seven times!  

It looks to me like the problem might actually be with the usb_storage module.  If I watch /var/log/messages, I can see usb_storage register 7 different devices (sda through sdh) for the same piece of physical hardware.

I'm working with a newly-installed ubuntu 5.04 system.

A quick search in the forums didn't reveal much.  Has anyone else seen this?  Is this a new bug, or something wrong with my machine?  If it's a bug, where do I report it?

---

