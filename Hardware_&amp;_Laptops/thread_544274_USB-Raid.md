---
title: "USB-Raid"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by zeroflag on 2007-09-06
Hi everyone,

since my rather extensive eplanation of my project ([here]("http://ubuntuforums.org/showthread.php?t=543429")) didn't get me any answers, I'll try it again with a short, straight forward question:

Is it possible to setup a (soft)raid0 with 2 (or more) external USB devices?

And if it is...

Is it possible to boot from such an USB raid? Where would I put the boot loader?

so long.

---

### Post by kidders on 2007-09-07
Hi there,

> **zeroflag said:**
> Is it possible to setup a (soft)raid0 with 2 (or more) external USB devices?Yes, Linux will let you construct a RAID array out of almost anything ... you don't even have to use physical devices, or confine yourself to things connected to one computer.

Whether using a particular device is a *good idea* is a different question though. In my view, the USB interface is too slow for RAID. Using USB devices with no moving parts (ie flash memory) would, as well as being slow, probably cause them to overheat & fail prematurely.

> **zeroflag said:**
> Is it possible to boot from such an USB raid? Where would I put the boot loader?In theory, yes ... but again, it probably wouldn't be a good idea. RAID exists primarily to improve reliability, so storing an array on multiple USB devices seems sort of counter-intuitive.

You could put your bootloader anywhere you wanted, really ... an internal hard drive, an optical disc, and so on. Whether you could use one of the array's USB devices would depend on whether your BIOS supports booting off the USB bus.

Anyhow, I hope that helps a little. I suppose the short answer is that what you want to do is *possible*, but it would be slow, untrustworthy, short-lived, and difficult to set up.

---

