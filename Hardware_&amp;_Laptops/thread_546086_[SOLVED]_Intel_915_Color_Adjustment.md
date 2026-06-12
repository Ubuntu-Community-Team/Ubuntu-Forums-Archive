---
title: "[SOLVED] Intel 915 Color Adjustment?"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by Andreas1 on 2007-09-08
Hello Community!

I was wondering if there is a way to adjust the color of my display...

I have an Intel 915 card (915resolution worked just fine) but my display looks a little too bluish by default.

In Windows there is some interface provided with the Intel drivers where i can set
brightness
contrast
gamma
of each RGB channel separately, where i just turn the contrast of the Blue Channel a little lower and everything looks fine.

Is there a way to do this in Linux? Some Tool?
Do i have to install the Drivers provided by Intel for Linux or are they installed anyway on ubuntu feisty (for everything already works fine)?

---

### Post by julian67 on 2007-09-08
You might like to try [GAMMApage]("http://www.pcbypaul.com/software/GAMMApage.html")

You might also like to read [Looking good: Monitor calibration under X]("http://www.linux.com/articles/113936")

edit: re drivers, they are installed anyway. You'll get used to that :-)

---

### Post by Andreas1 on 2007-09-09
Now I have it:
it is called xcalib [http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/]("http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/")

a mere gamma correction tool (for some reason there are plenty of those) would not have done it, but with this one you can set also contrast and brightness of your display, just what i looked for

downloaded the linux-precompiled version, placed it "/bin/xcalib", opened terminal and typed something like "xcalib -blue 1.0 0.0 0.95 -a" :)

after reading a few articles on monitor calibration i understand that the values this program refers to are not graphic-card-specific, so this should work for all graphic cards (correct me if that is wrong).

@julian67 re drivers: thanks, i think i could get used to that :)

---

### Post by julian67 on 2007-09-09
> **Andreas1 said:**
> ........
downloaded the linux-precompiled version, placed it "/bin/xcalib", opened terminal and typed something like "xcalib -blue 1.0 0.0 0.95 -a" :)

looks good, thanks for posting the info

---

