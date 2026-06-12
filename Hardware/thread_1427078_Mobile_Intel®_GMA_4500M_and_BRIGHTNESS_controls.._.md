---
title: "Mobile Intel® GMA 4500M and BRIGHTNESS controls.. sigh"
date: 2010-03-11
forum: Hardware
---

### Post by prdolino on 2010-03-11
Hi,

I have been trying to solve this problem for the past 6 hours with no success. I have been messing around with my:

/etc/default/grub

file as suggested on some of the other threads and nothing seems to work. I also tried Kubuntu, thinking that may do something. I am also quite the rookie when it comes to this (I think).

I am using Ubuntu 9.10 (main & universe). EVERYTHING works great other than the brightness and I am out of ideas. Does anyone have any ideas? It would be greatly appreciated. I guess it is time to get some sleep before waking up for work in a few hours...

Also, my laptop is:

[http://www.lge.com/ca_en/computer-products/notebooks/LG-r400-R460-L.AHC6WA9.jsp](http://www.lge.com/ca_en/computer-products/notebooks/LG-r400-R460-L.AHC6WA9.jsp)

Everything works great but the brightness is ssooo bright I am burning my retinas!! :P

Thanks again,
Nino.

---

### Post by Rustybolts on 2010-03-19
Bump
Same problem as above have been looking for many weeks same graphics chip on a acer 5332

---

### Post by ahb on 2010-03-19
Not sure on the recommended way, but have you tried xgamma?

From console:

Show gamma level: xgamma

Set it to x: xgamma -gamma x

To make this work after restarting X, see:
[http://ubuntuforums.org/showthread.php?t=414180](http://ubuntuforums.org/showthread.php?t=414180)

hth.

---

### Post by prdolino on 2010-03-21
ahb: Thanks! That is somewhat of a fix for now! Not a very "pretty" fix but at least my retinas will be salvaged during those late nights.

Guess I will have to hope that Lucid will have my video card all sorted out.

---

### Post by pingu1 on 2010-07-01
Could you guys not adjust the brightness in the system-menu?
Was it just the buttons for adjusting it or was it not possible to adjust it at all?

Is this fixed in 10.04 ?

---

### Post by pingu1 on 2010-07-01
Could you guys not adjust the brightness in the system-menu?
Was it just the buttons for adjusting it or was it not possible to adjust it at all?
 
Is this fixed in 10.04 ?

---

### Post by Rustybolts on 2010-07-09
10.04 didn't fix it no. Sigh!

---

### Post by gbrubal on 2010-07-09
I have the same problem with the same card on a hp pavillion dv3. No solution found (i am dying!).

---

### Post by MikeyDL on 2010-07-27
just installed on my new aspire with a 4500M.  I get the feeling that Intel GMA 4500M are in the permanently screwed category since this seems like a long term issue that hasn't been solved and may not ever be solved.  :-(

---

### Post by Sonador on 2010-07-28
i successfully use this workaround: [http://ubuntuforums.org/showpost.php?p=9614117&postcount=3](http://ubuntuforums.org/showpost.php?p=9614117&postcount=3)

---

### Post by marquinos on 2010-12-30
This works perfect for my laptop ACER TM 5735 Graphic card T4500M, with Ubuntu 10.10 64 bits:
[http://ubuntuforums.org/showpost.php?p=10112062&postcount=6](http://ubuntuforums.org/showpost.php?p=10112062&postcount=6)
Best regards.

---

