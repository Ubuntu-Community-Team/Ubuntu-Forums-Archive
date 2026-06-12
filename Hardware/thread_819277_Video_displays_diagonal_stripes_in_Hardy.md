---
title: "Video displays diagonal stripes in Hardy"
date: 2008-06-05
forum: Hardware
---

### Post by cov on 2008-06-05
Hi,

I have installed Hardy Heron on a new computer and the video display is corrupted.

The scanline appears to be incorrect resulting in the display being  in diagonal stripes across the screen.

It worked fine under Gutsy.

I can't remember the command to display the make and model of the (onboard) video card, but if somebody could jog my memory I will use it to discover these details and post them here.

Many thanks,

dave Coventry

---

### Post by cov on 2008-06-05
The command I was looking for was, of course, 'lspci'.

The video card:
VGA compatible controller: VIA Technologies, Inc.
Chrome9 HC IGP (rev 01)

The error message I'm getting in Xorg.0.log:

(EE) CHROME(0): Unknown Card-Ids (3371| 908|1975); please report to [email]openchrome-users@openchrome.org[/email]
(EE) [drm] drmOpen failed.
(EE) CHROME(0): [dri] DRIScreenInit failed.  Disabling DRI.

---

### Post by cov on 2008-06-06
Okay,

Since nobody appears to have any ideas, I've reported it to [email]openchrome-users@openchrome.org[/email] as requested....

---

### Post by J-Ram-z on 2008-10-08
Just to let you know -- you are not alone. I haven't found an answer to this one and I have eight computers working as LTSP Clients that are unusable.

I you come up with something, I'd love to hear about it!

Thanks,

J.R.
Cape Town

---

