---
title: "Nvidia GLX-177 disabled package - 8.04 to 8.10"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by shawfield on 2009-05-04
Hi

When trying to upgrade 8.04 to 8.10 in order to finally arrive at 9.04 after a further upgrade, I upgraded today & got the expected problem with Nvidia drivers, that I got when 8.10 first came out.

Can anyone tell me what the fix is for the Nvidia drivers under 8.10 ?
I now have a 'split' screen where the left hand side of the screen is in a separate window to the top of the screen & the right hand side of the screen. Basically, an unusable system, that is flickering horribly.

I'd previously upgraded to 8.10 months ago, but when these problems arose, reverted back to 8.04 where they work perfectly & stupidly thought that since now 9.04 is out, the 8.10 nvidia issues would be solved by now. Ooops...wrong.

Help anyone ?
Thanks

---

### Post by AlecJ on 2009-05-04
Yes I did this see here
[http://ubuntuforums.org/showthread.php?t=1142976](http://ubuntuforums.org/showthread.php?t=1142976)

---

### Post by shawfield on 2009-05-04
Hmmmmm

Bit scary that one !

Sounds like an install off the 9.04 live CD & lose my old emails.

Or does 9.04 also have the same problem ?

---

### Post by AlecJ on 2009-05-06
> **shawfield said:**
> Hmmmmm

Bit scary that one !

Sounds like an install off the 9.04 live CD & lose my old emails.

Or does 9.04 also have the same problem ?

I'm on 9.04, so yer same deal. It's these all new binary files for Linux, old hat in Windoz. I guess in time it will get into the kernal, but there not free yet.

That xorg.conf will work, remember it's just there to inform/invoke the binary driver.

---

### Post by shawfield on 2009-05-07
I had to install 9.04 from the live CD & then the system detected my Nvidia card & offerred me the correct drivers.

8.10 simply didnt do that. It just disabled the recommended drivers & gave no options.

---

### Post by AlecJ on 2009-05-07
good, so your on Nvidia 180.51 now then?

---

### Post by shawfield on 2009-05-07
Yes indeed. 9.04 seems much more 'intelligent' than 8.10.

In fact it works really well on my little Acer netbook as well.

---

