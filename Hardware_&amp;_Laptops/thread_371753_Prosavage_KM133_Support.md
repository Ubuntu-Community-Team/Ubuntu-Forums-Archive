---
title: "Prosavage KM133 Support"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by mwillett on 2007-02-27
Let me start by saying I am pretty much a newbie to Linux but I have been around computers most of my life so figuring things out is a part of my daily routine.  

I recently installed Ubuntu on an old clunker HP that I had laying around, it’s a 1.33 ghz AMD with 512 RAM and a S3 ProSavage KM133 onboard Video Card with 32 Megs of RAM.  With this PC I had to buy a monitor so I went over to best buy and got a great deal on a Westinghouse 20 inch LCD that runs a native resolution of 1400x1050.  My problem is that I can’t get xwindows running at that resolution and gnome looks and behaves like crap.  I realize that this is an older computer and I might not be able to get this thing running at Native resolutions but I figured I would ask.  Any hacks I can make to xorg.conf?  I have enabled/disabled the VideoBIOS thinking that might do the trick but it only broke xwindows.

The Short Question:
[B]Has anyone got the ProSavage KM133 to run in 1400x1050 resolution?
[/B]
Thanks guys and I look forward to working with you all.

---

### Post by PowerRanger on 2007-05-14
in your xorg.conf, in Device section add:

```
Option "UseBIOS"  "false"
``` 

and reboot (or maybe just restart gdm) 


It worked for me @1440x900...

---

