---
title: "intrepid + dell latitude e4200 (intel mobile 4 chipset): slow framerate"
date: 2008-12-24
forum: Hardware
---

### Post by leifer on 2008-12-24
I've just installed the standard desktop version of intrepid on a Dell Latitude E4200 with 3GB ram and a 64GB SSD.

The window movements appeared slow and choppy, so I tested the framerate with glxgears and came up with an average of 180 frames/second, which is markedly slower than my previous Dell Latitude D420 running hardy which gets about 620 frames/second.

These results are consistent accross gnome, kde, or xfce.

According to lspci (full log attached to this post), the graphics chipset is recognised by the kernel as

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

According to Xorg.0.log (full dump attached), X is using the following intel driver:

  Module intel: vendor="X.Org Foundation"
       compiled for 1.5.2, module version = 2.4.1

If it's of any use, I also enclose my apt.sources.

My question: why is the framerate so slow and what can I do about it?

I would of course be happy to provide more diagnostics upon request.

Many thanks in advance for any suggestions!

-James Leifer

---

### Post by rxl881 on 2008-12-24
Hi, 

I'm also seeing a very similar problem with a fresh install of Intrepid on a Samsung R510 laptop - e.g. very low frame rates etc. 

lspci is showing the graphics chipset of this laptop as:
 "00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)". I am also seeing very choppy, flickering frames with glxgears, with speeds of about 149fps :(

The output of Xorg.0.log seems to be pretty identical to that of the previous poster.

Additionally, I can only get a maximum res. of 1024x768. 

Any suggestions?

Many thanks

R

---

### Post by avilella on 2009-01-25
Hi,

I took the liberty of creating a launchpad team for the people who own or develop for the Dell Latitude E4200/E4300 laptops, so that we can have more visibility upstream when having to ask for patches or support.

[https://launchpad.net/~e4200-e4300](https://launchpad.net/~e4200-e4300)

I'll be sending a couple of messages to ubuntuforums and notebookreview forums to gather the ~15 users I've identified so far.

Cheers,

Albert.


> **leifer said:**
> I've just installed the standard desktop version of intrepid on a Dell Latitude E4200 with 3GB ram and a 64GB SSD.

The window movements appeared slow and choppy, so I tested the framerate with glxgears and came up with an average of 180 frames/second, which is markedly slower than my previous Dell Latitude D420 running hardy which gets about 620 frames/second.

These results are consistent accross gnome, kde, or xfce.

According to lspci (full log attached to this post), the graphics chipset is recognised by the kernel as

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

According to Xorg.0.log (full dump attached), X is using the following intel driver:

  Module intel: vendor="X.Org Foundation"
       compiled for 1.5.2, module version = 2.4.1

If it's of any use, I also enclose my apt.sources.

My question: why is the framerate so slow and what can I do about it?

I would of course be happy to provide more diagnostics upon request.

Many thanks in advance for any suggestions!

-James Leifer

---

### Post by jfr1tz on 2009-01-26
lenghty discussion about the gma 4500 series [here]("http://ubuntuforums.org/showthread.php?t=963386")

---

