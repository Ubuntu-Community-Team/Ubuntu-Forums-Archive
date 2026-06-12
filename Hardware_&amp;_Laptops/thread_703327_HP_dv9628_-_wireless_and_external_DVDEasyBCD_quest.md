---
title: "HP dv9628 - wireless and external DVD/EasyBCD question"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by gopher38 on 2008-02-21
Hello,

New to Linux and first time installing on a laptop (HP DV9628nr - AMD Turion).  Running into two problems and would appreciate help.

Problem 1: wireless - I've read through quite a few of the threads (here and elsewhere) and I THINK that I'm not that far off, but I can't get it to work.  Have broadcomm wireless.  If I understood correctly, I have to use ndiswrapper, which I've installed.  I read that I had to use bmcwl5 with ndiswrapper, but my machine only had bmcwl6, so I tried using that.  Machine boots and the wireless LED is on, but when I try to connect, it doesn't see the router (signal strength shows null).  It turns and turns, and eventually gives up, and the LED goes off.  I've turned off security of the router, and tested with an old XP laptop, which connects fine.  

In some of the threads, I read that bmcwl6 doesn't work, even if it is on your machine, so I downloaded and extracted bmcwl5, and tried to use that.  First problem, dniswrapper alerts that this is an invalid driver (so perhaps bmcwl6 is correct after all), and anyway, the behaviour is the same (doesn't see signal and LED goes off).

Anyone know what I'm doing wrong?

Problem 2:  I used Easy BCD to set up Vista-Ubuntu dual boot (chained boot, I think it's called.  I first have a chance to select Vista or Linux, defaulting into Vista.  Then passes to Grub , which then allows me to select Ubuntu or Vista-longhorn, defaulting to Ubuntu).  If I have an external DVD player plugged in an USB however, it doesn't even make it to the first selection.  It blocks, and then unplugging the DVD allows it to move forward.  This never happened when I had just Vista installed, so either Ubuntu or EasyBCD is messing something up.  EasyBCD seems more logical, since I never even make it to Ubuntu, but I can't see any options in EasyBCD to try to change this.  

If someone else had this issue, please let me know what you did.

Thanks.

---

### Post by gliderdad79 on 2008-05-19
Same thing is happening to me too for the wireless. I had 7.10 working for a long time, ran the upgrader to 8 and it didn't work even after adding the few extra steps added. I reinstalled 8 with a fresh install and still cant get it working.

---

