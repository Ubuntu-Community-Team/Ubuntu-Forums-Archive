---
title: "Asus A6R: fglrx and usb problem"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by sturmdogg on 2006-07-11
Does anyone here use an Asus A6R and Ubuntu, and has solved the problem with the usb devices hanging / freezing when using the fglrx driver? I see some posts where people have been successful in installing the said driver, but I have no idea if they're suffering the same problem with the usb as I am.

---

### Post by sturmdogg on 2006-07-12
anyone? help?

---

### Post by leoneri on 2006-07-13
yeah, fglrx has in issue. why don't you use "ati", since ubuntu 6.06, this driver from Xorg is running without problem.

rgrds,

---

### Post by sturmdogg on 2006-07-13
*sigh* oh well...I guess being 2d only with working usb ports is better than having 3d with screwed up usb ports :P

---

### Post by leoneri on 2006-07-13
:D :D :D :D perhaps patience will be the answer for that... :D :D :D :D
maybe the next release of ubuntu or fglrx will fix this issue.. 

rgrds,

---

### Post by Eversmann on 2006-07-13
Mannnnnn, i have the same issue on my fujitsu amilo l1310g. Looks like everyone that have ati chipset on his laptop have the same issue. I'm "fighting" against that since 3 weeks. Right now i'm testing another "fix" to see if it works...... It's a well known problem, confirmed by canonical, bug level "critical".

I read somewhere that could be an issue with our kernel if it has the ati support enabled or something like that.

Anyone tried with custom kernel compiled by himself? 2.6.16?

Kororaa 0.2 hangs on boot.......

---

### Post by didobuntu on 2006-07-13
Hello,

I never had problems with Asus laptops ... I actially have the W2Jc ...

What video card have your Asus A6R ?

---

### Post by sturmdogg on 2006-07-14
didobuntu: I have the x200m on my laptop. 

If only we can change / upgrade vidcards on laptops ;)

Eversmann: How can we tell if canonical has fixed the bug? Is there a dev blog somewhere?

---

### Post by hygraed on 2006-07-23
> **sturmdogg said:**
> didobuntu: I have the x200m on my laptop. 

If only we can change / upgrade vidcards on laptops ;)

Eversmann: How can we tell if canonical has fixed the bug? Is there a dev blog somewhere?

I have this exact problem, and, indeed, this exact video card. I have a Toshiba Satellite L25-S1194. Apparently the problem is pretty much universal.

---

### Post by murak on 2007-07-02
One more with ati 200m and the "hanging usb"-problem here. 

Thank god that the touchpad still works.

---

### Post by murak on 2007-07-03
Well, Ubuntu wanted to update and I let it. After a reeboot the ati fglrx driver worked like a charm! Is this a newly available update and if so, are other people also getting the driver to work?

But, desktop effects wont start, it just says "The composite extension is not available."

EDIT Then I followed this guide [http://ubuntuforums.org/showthread.php?t=321766&highlight=ati+berryl](http://ubuntuforums.org/showthread.php?t=321766&highlight=ati+berryl)

wich made my day, desktop effects now works on my a6r. But not the spinning cube stuff, BUT I have a feeling that will get sorted out very soon..

EDIT 2: After following this guide [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314) Compiz Fusion (including the spinning cube) works. AND my usb no longer stops! I recomend other users of A6R or ppl with Xpress 200M to try this guide, chanses are its gonna work for u to. GL!

Despite its problems, Im starting to like this os.

---

