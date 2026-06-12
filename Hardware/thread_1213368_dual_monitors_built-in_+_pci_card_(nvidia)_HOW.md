---
title: "dual monitors: built-in + pci card (nvidia) HOW?"
date: 2009-07-14
forum: Hardware
---

### Post by Nazaroo on 2009-07-14
Okay I have a box with a built-in vid card and also a PCI slot with an NVIDIA Gforce 440.

In the past I had no problem getting both cards on in Win2K, by toggling the default card (AGP/PCI) in the BIOS and rebooting, then diddling with desktop properties.


Is there a link to an explanatory page or a procedure to get both cards up (extended desktop) on Linux (Ubuntu/Debian)?  I am desperate to get productivity back here.

I really really really want to dump Win2k for good, since I have no budget for $400 OS/Upgrade.  For that I could buy another computer.


thanks
Nazaroo

---

### Post by Nazaroo on 2009-07-14
,,,following up on a lead in another dual monitor thread, I ran the this command in a console:

```

lspci | grep VCA

```

This was the result:

```


00:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce 4 MX 440] (rev a3)

00:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]


```

The first is the PCI card (MX440) , the second is the onboard VGA (ProSavage8).

So far so good.  It seems the OS recognizes both VGA cards.  
Problem seems to be that right now the nVidia Drivers are overriding the Linux generic driver, and there doesn't seem to be an option on the nVidia Dialogue box.

There is a "search for monitors" button, but this doesn't seem to find anything (perhaps it only searches for monitors hooked up to an nVidia controller, and so skips the obvious onboard unit.

Any ideas?

thanks
Nazaroo

---

