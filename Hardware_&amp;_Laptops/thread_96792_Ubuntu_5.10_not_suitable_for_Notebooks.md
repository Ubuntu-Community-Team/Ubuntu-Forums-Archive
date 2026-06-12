---
title: "Ubuntu 5.10 not suitable for Notebooks?"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by eur on 2005-11-29
during installation on a Notebook (Lion/Mitac 7521T) currently the CDR drive stops, LCD screen is becoming black and after few seconds a weird textile structure appears on the screen. From there Notebook is frozen and nothing other can be done than switch it off.

Heeelp !!!

Bis dissapointed from so much "easy fo beginner claimed system:confused: "

---

### Post by kverde on 2005-11-29
well, it works REALLY well on my Dell 700m.  (Except for TVout, oh well).

But, hardware support really is the last major hurdle for linux--and its getting even better.  But you can't blame Ubuntu for the situation.  Few of the hardware vendors care to ensure that their products work with anything other than "The Other OS".  Until hardware vendors know that people like me will buy their product if it is "Ubuntu Certified", then it will continue to be a challenge to support every peice of poorly designed hardware-----but Ubuntu does an amazing job even now.  Sorry that the laptop you have isn't well supported.  But mine is.

---

### Post by lerrup on 2005-11-30
[QUOTE=eur]during installation on a Notebook (Lion/Mitac 7521T) currently the CDR drive stops, LCD screen is becoming black and after few seconds a weird textile structure appears on the screen. From there Notebook is frozen and nothing other can be done than switch it off.

Heeelp !!!

Bis dissapointed from so much "easy fo beginner claimed system:confused: "[/QUOTE]

Can you say at what point that it freezes, etc?  SOmeone might be able to help.

Good luck, and I can't think this is unsolvable.

---

### Post by nocturn on 2005-11-30
[QUOTE=eur]
Bis dissapointed from so much "easy fo beginner claimed system:confused: "[/QUOTE]

I'm sorry to hear you had troubles.  Portables are sometimes a problem, specially some models which deviate quite a bit from public standards (like ACPI).  

Ubuntu actually runs quite well on a number of systems, like my HP Pavilion, but some others require a bit of tweaking. 

Your system should work rather well though, can you explain where it stops (during install, at boot time?)

---

### Post by nocturn on 2005-11-30
At the boot screen, can you try to add the parameter:
video=vga:off

This may help.

---

### Post by kaamos on 2005-11-30
Or you can try also: "linux vga=771". This worked for me.

---

### Post by luca_linux on 2005-11-30
Breezy works really really well on my laptop (Asus M6N): everything works out of the box, even the buttons!

---

### Post by too_sick_for_you on 2005-11-30
I am using it on my Acer Aspire 3000 notebook. Works great!

---

### Post by betamax on 2005-11-30
Runs great on my humble IBM T23.
Took a few tweaks (apci..) to get running perfect though.

---

### Post by niobe_logos on 2005-11-30
It may be that your Lion/Mitac 7521T has just enough odd hardware in it that Ubuntu can't support it. For more info on running Linux on it, you may want to check out the pages listed at [TuxMobil.org]("http://www.tuxmobil.org"). This site lists pages about Linux installations for just about every brand of laptop. The pages are people's personal notes on what worked, and what didn't for installing Linux. Surprisingly, Mitacs are listed, check it out:

[http://tuxmobil.org/mitac.html]("http://tuxmobil.org/mitac.html")

Most of the well-known laptop brands will run Ubuntu with varying amounts of success. My Toshiba Satellite did most functions fine out of the box, including wireless. If you decide to get another laptop, Toshiba, Dell, HP, IBM Thinkpad, and a bunch of other brands will run Ubuntu with few or no problems.

---

### Post by ex` on 2005-11-30
[QUOTE=niobe_logos]It may be that your Lion/Mitac 7521T has just enough odd hardware in it that Ubuntu can't support it. For more info on running Linux on it, you may want to check out the pages listed at [TuxMobil.org]("http://www.tuxmobil.org"). This site lists pages about Linux installations for just about every brand of laptop. The pages are people's personal notes on what worked, and what didn't for installing Linux. Surprisingly, Mitacs are listed, check it out:

[http://tuxmobil.org/mitac.html]("http://tuxmobil.org/mitac.html")[/QUOTE]
Another handy site for this is [http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/)

Could you perhaps provide us with a complete description of the problem and the steps you took before it occured?

---

### Post by maxper on 2005-11-30
i have a compaq Evo N1020v 256MB RAM and it appears to work fine! :D

---

### Post by jdong on 2005-11-30
[QUOTE=kverde]

But, hardware support really is the last major hurdle for linux--and its getting even better.  But you can't blame Ubuntu for the situation.  Few of the hardware vendors care to ensure that their products work with anything other than "The Other OS". [/QUOTE]
Hardware support has been seeing rapid improvement in Linux over the past 5 years... It used to be that maybe 1 or 2 computers at the typical store could be booted up with a Knoppix LiveCD, and now it's just getting hard to find a system Linux won't work on to some degree!


And the hardware vendor comment, you've hit the spot but it's not that vendors don't write Linux drivers is the problem. For most vendors, the Linux market is so small that targeting it would be a bad idea business/financial wise. However, the problem is that vendors do not release the **necessary information** about their hardware so that others can write drivers for it... Ask any Linux kernel developer, or browser lkml when a thread about hardware support comes up. Most of them are more than thrilled to write the drivers, as long as vendors release some documentation as to how their hardware works!

Many of the drivers you are using under Linux have been painstakenly written through a tedious reverse engineering/guessing process, so we have to appreciate how well they work.

---

