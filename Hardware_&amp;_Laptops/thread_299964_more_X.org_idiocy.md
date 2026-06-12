---
title: "more X.org idiocy"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by draeath on 2006-11-15
Well, I just installed xubuntu 6.10 and everything was working fine. Untill I updated my kernel modules. Now, my display refuses to operate at 1280x1024 as it was before.

My [xorg.conf]("http://keleus.freeshell.org/xorg.conf")
My [Xorg logfile]("http://keleus.freeshell.org/Xorg.0.log")

Of paticular notice and/or irritation on lines 771 and 772 of the log:
```
(WW) RADEON(0): Option "HorizSync" is not used
(WW) RADEON(0): Option "VertRefresh" is not used
```
](*,) 

So, what exactly am I supposed to do? I overrid the false DDC detections on my displays by forcing it as CRT on primary with nothing else (actual layout is an unused and hence turned off laptop display panel, with a CRT on secondary connector), that didn't work. Then, i forced it to use the laptop panel on primary and the crt on secondary, set the CRT as screen 0, and set CRT2Hsync and CRT2Vrefresh properly. No change. You can see some of the leftovers commented in my xorg.conf

I crawled through 'man xorg.conf' and 'man radeon' with no success.


All I want to do is use the CRT hooked up to the VGA output on the laptop. I don't even want to know the built-in LCD exists. How do I do this? Besides getting a computing system that isn't quite so 'challenged' as an HP laptop? (This is used as a desktop replacement)



... on a side note, firefox wants to use subpixel hinting for Anti Aliasing it seems. Interestingly enough, this doesn't work on CRTs, and also the driver doesn't support using that on my LCD (for this paticular chipset, anyways). How can I fix that?

---

### Post by Compaq Armada 7800 on 2006-11-15
i had some trouble with FC5 a while back like that. did you try that xorgconf command? do an 'init 3' and then run your X-setup command and then gdmconf and them go 'init 5'


technically speaking, there is no vert/horz refresh rates on LCD's, it is in the X scripts as a dummy or filler. it may one day be a burden to us all though.

---

