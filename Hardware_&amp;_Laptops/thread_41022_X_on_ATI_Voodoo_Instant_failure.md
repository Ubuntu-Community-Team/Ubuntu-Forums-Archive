---
title: "X on ATI Voodoo: Instant failure"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by Smotricz on 2005-06-11
Hi! This is a, umm, "weakness report" and a "how to get around it".

I tried installing Ubuntu on this rickety old box with 400 Mhz Centrino and 128 MB RAM, previously running Win98. The pre-owner was a gaming freak so there are *two* ATI 3D Rage IIc (= "Voodoo") cards in the box. Apparently you can hook them together for double power.

The installation went smoothly until it tried to switch into X. "Screen not found", "device not found". "X -config" didn't do any better, either. I apt-get-install'ed libglide2 and libglide3, after that it came to "no output driver found". Bah!

I tried booting the Knoppix live CD, hoping to get a valid X config file. Knoppix declared a frame buffer and worked like a charm, but the config file wasn't sufficiently compatible.

Finally, I changed the "driver" in "device" from "glide" to "ati", and everything went fine.

OK, the problems with getting X running on all kinds of devices are legion. Does anyone care? Should I report this in the bug section of the official Ubuntu site? Or maybe to X.org?

---

### Post by voidlogic on 2005-06-11
I'd repot it to both. I'm confused, I though 3DFX made the Vodoos. When you changed it to 'ati', were the cards still running in SLI mode? This in interesting, becuase nVidia's (who bought bought 3DFX) new SLI video cards will not operate in SLI mode under linux (lack of driver support). They had new features every driver, so I'm not concerned. Thanks for sharing the interesting experence.

voidlogic

----------------------------------
Help Please! 
[http://www.ubuntuforums.org/showthread.php?p=202288#post202288](http://www.ubuntuforums.org/showthread.php?p=202288#post202288)
 ](*,)  ](*,)  ](*,)

---

### Post by markuman on 2005-06-30
[QUOTE=voidlogic]I'd repot it to both. I'm confused, I though 3DFX made the Vodoos. When you changed it to 'ati', were the cards still running in SLI mode? This in interesting, becuase nVidia's (who bought bought 3DFX) new SLI video cards will not operate in SLI mode under linux (lack of driver support). They had new features every driver, so I'm not concerned. Thanks for sharing the interesting experence.

voidlogic

[/quote]

very interessting what you are writing (nvidia SLI is not supportet on linux).
because SLI don't work on Voodoo 4 / 5.
still on voodoo 2...perhaps on voodoo 3 too.

well. for 3Dfx graphics chips still use Glide Library to have 3D support. never mind what producer had made your 3Dfx card.

---

### Post by Vampyre on 2005-10-07
yep yep yep , i just lernt the hard way ATI + Voodoo dont click well with ubuntu , CANNOT belive i decided to whack me redhat box and try this.

Redhat 9 worked fine :-( , but ubuntu dont ... so i guess back to redhat for me.

Hope this problems gets sorted , ubuntu seemed like a  good project to support.

Cheeers
Vampyre

---

