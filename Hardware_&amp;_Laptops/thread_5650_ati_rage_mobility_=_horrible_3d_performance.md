---
title: "ati rage mobility = horrible 3d performance"
date: 2004-11-21
forum: Hardware &amp; Laptops
---

### Post by stateq2 on 2004-11-21
ok...I never could get the fglrx driver working, so I just went ahead upgraded to xorg and hoary.  In my xorg config file, i'm using the "ati" driver.  In games like tuxracer, I'm getting less than 1 fps.  Is there a software problem, or is my card just that crappy?

I have a compaq armada m700 laptop (850mhz p3, 512mb ram), and here's my card according to lspci:
```

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

thanks for any info.

---

### Post by stateq2 on 2004-11-21
no info?  i can't even find any reviews of this card online...please help  :(

---

### Post by jdong on 2004-11-21
yeah, unfortunately that's the case with ATI cards... X.org is also lacking in 3d acceleration for this card.
 
 
 DRI may help.

---

### Post by daniels on 2004-11-22
[QUOTE=jdong]yeah, unfortunately that's the case with ATI cards... X.org is also lacking in 3d acceleration for this card.[/QUOTE]No, not at all.  IIRC the Rage Mobility is an r128, which is fully supported for DRI in X.Org, and even XFree86.  You will get full support for it if it's set up right, but the subject says it all -- don't expect any form of good performance from it.

---

### Post by mr_ed on 2004-11-23
It's the card.

The Rage Mobility is only supported in XFree with the GATOS drivers.

When I upgraded from XFree to XOrg, it almost doubled my glxgears score.  Of course, that was still *terrible* but it was better than before.  :(

---

### Post by stateq2 on 2004-12-05
**UPDATE**

I fixed my problem :D
[http://www.ubuntuforums.org/showthread.php?t=7200](http://www.ubuntuforums.org/showthread.php?t=7200)

---

