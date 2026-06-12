---
title: "ATi x850 XT PE issues - won't use fglrx"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by wermerskoch on 2006-03-21
Hi everyone,
  I'm tring to get my ATi card to work with the proprietary ATi drivers.  Every installation I try seems to go smoothly, but then I use the command fglrxinfo, and it shows it's using the mesa stuff.  Here's what I'll I've tried:  I downloaded the latest driver from their website, and followed these instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

I followed them to the T.  Three times.  After the first couple of attempts, I used this guide:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

After that didn't work twice, I reinstalled Ubuntu, and tried the first guide again (because it has worked for me in the past using a Radeon 9800).  I should add that on this last try, after I installed it on the xorg.conf there were two device entries for the video card -- one using the ati driver and one using the fglrx driver.  I changed the ati one to fglrx -- again, no luck.

Please help if you can, I've been working on this for the past couple days -- I don't want it to take up my whole spring break!  If you can help me, I'll give you a dollar.  \\:D/ 

Here's my system specs, my xorg.conf, and my Xorg.0.log (sorry I don't know how to embed them in this page, so I had to compress and attach them...)

epox 4PDA5 motherboard
P4 3.0 Ghz
1.5 GB RAM
ATi Radeon X850XT Platinum Edition
Running Ubuntu Breezy, everything up-to-date

---

### Post by wermerskoch on 2006-03-21
Update:
  I just used EasyUbuntu (for which my ego took a severe beating), with the same results -- still showing the mesa stuff.

---

### Post by wermerskoch on 2006-03-22
Bump...  Please help!  ](*,)  I know most of you out there know more than I do about this.  ;)

---

### Post by wermerskoch on 2006-03-25
Sorry to keep bumping this to the top, but I'm getting a bit desparate. :(

---

### Post by mrprefect on 2008-05-20
I'll bump this one, I'm having nothing but trouble with the ATI drivers. Trying to get dual monitors on my ATI x850, as soon as the ATI drivers are loaded I lose the screen and have to replace the xorg.conf to get anything back with the vesa drivers.

---

