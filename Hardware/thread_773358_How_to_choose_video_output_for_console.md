---
title: "How to choose video output for console"
date: 2008-04-28
forum: Hardware
---

### Post by justdave72 on 2008-04-28
I have an Intel 845GM video card with two video outputs on it (Mac Mini Core 2 Duo, first is DVI, second is S-Video/Composite output).  For some reason they both show up as enabled, even though the first has nothing plugged into it.  Of course, the kernel picks the wrong one for the console, so I have no text console at all.  I got around this in X by putting a Monitor section for the empty one in the xorg.conf file with an Option "Ignore" "True", but that doesn't help my text console.  Does anyone know if there's something I can put on the kernel command line in grub to tell the video card to use the second output by default?  Been googling around for a while and not finding anything useful.  Thanks!

---

### Post by denen.cyg on 2009-04-20
let's try again... even though its april 2009 now...

does anyone know a solution to justdaves and my problem... circumstances are a bit different in my case... laptop screen's broken...
got an onboard graphic chip aswell and want to use secondary vga output as main... well at least be able to see console on it...

---

