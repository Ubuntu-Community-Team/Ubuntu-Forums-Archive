---
title: "Macbook VS Compaq V2000"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by cosine7 on 2006-08-03
I was thinking about a new laptop which i need for uni. with the new MacBooks out i was think of getting the 1.8, which has the intel graphics chip set, but i can get the compaq for almost half the price AMD 1.8. Does anybody now how Dapper will run on these machines? The compaq use ATI Mobile, am i going to have trouble? (I still have not got my desktop ATI runng 3D)

Thoughts ppl?

(PS I am a Uni student, so primary reasons for both machines is size, i need to have them easily fit in a backpack)

---

### Post by huygens on 2006-08-03
Hi,

I would suggest the Mac because - correct me if I'm wrong - the GMA950 graphic chipset has an open source driver which is supported by Intel.
For ATI, you have an open source driver not supported by ATI and with which I could not make any 3D acceleration, and a proprietary driver which is pretty unusable on my Radeon Mobility 9000 :(

Thus, now I tend to run away from ATI...

Also, having seen the MacBook and its design, I would not hesitate too much (actually I'm most probably going to buy one...)

Huygens


PS: this is my own personnal opinion. If I have to choose between the compaq and the apple, I would choose the apple. But, it might not be the right solution for you.

---

### Post by cosine7 on 2006-08-03
> **huygens said:**
> Hi,

I would suggest the Mac because - correct me if I'm wrong - the GMA950 graphic chipset has an open source driver which is supported by Intel.
For ATI, you have an open source driver not supported by ATI and with which I could not make any 3D acceleration, and a proprietary driver which is pretty unusable on my Radeon Mobility 9000 :(

Thus, now I tend to run away from ATI...

Also, having seen the MacBook and its design, I would not hesitate too much (actually I'm most probably going to buy one...)

Huygens


PS: this is my own personnal opinion. If I have to choose between the compaq and the apple, I would choose the apple. But, it might not be the right solution for you.


Thanks Huygens
To be honest i'm heading in the apple direction, just trying to justify the $$$$

---

### Post by yukito on 2006-08-03
> **cosine7 said:**
> Thanks Huygens
To be honest i'm heading in the apple direction, just trying to justify the $$$$

Apple tends to charge for the design, long battery life, and relatively light weight. They also tend to spend a lot of attention to details, whereas compaq s often cut corners to save money. I'd go with the mac any time. The question is: do you think its worth the extra money?

Until recently, I prefered to use my powerbook g3 (333MHz) over my acer simply because it was so perfectly built. Small, decent, very good battery life even after all those years and very reliable. Mac all the way.

---

### Post by huygens on 2006-08-03
Hi again,

Iv'e found a thread that might interest you: [http://ubuntuforums.org/showthread.php?t=222264&highlight=macbook](http://ubuntuforums.org/showthread.php?t=222264&highlight=macbook)

There you will find a link to a guy having installed his macbook with Ubuntu and happy with it.

There is also an interesting remark about an "evil Radeon 200M chipset", probably the same chipset as in the Compaq laptop...

Huygens

---

### Post by br420 on 2006-08-03
I have a v2000z running dapper right now and have been able to get everything working fairly easily using the forum. The macbook might be easier to get up and running (I wouldn't know), but I am just letting you know that the v2000z does work nicely and is substantially less expensive.

---

### Post by Noah0504 on 2006-08-03
Well, I have a Compaq V2615US that I bought at the end of June.  I haven't attempted installing Ubuntu yet because I'm not sure if the Broadcom wireless card will work (I tried out the Live CD and I don't think it is going to).

---

### Post by martinbures on 2006-08-04
I have a 2Ghz Macbook.  I bought it with the express purpose of putting Linux on it.  OS X is alright, but I use Dapper on my Opteron desktop and like it and want to use the same thing on the new Apple hardware.  Problem is that it Dapper has not quite caught up with the Macbook hardware.  It takes a bit more work to install.  You can get everything working except for a few things fairly easily.  Those things are the advanced touchpad features - two-fingered scrolling like under OS X.  I haven't seen anyone saying that they got this working - correct me if I am wrong - PLEASE!  I would love to have this feature working.  iSight requires a little work to get working.  On my box, it does not seem to throttle the cpu down when it is not very busy - so, it gets much hotter running Dapper than it does running OS X.  You have to do a special install and use an efi hack refit to, as I understand it, emulate a legacy BIOS.  There are occasional kernel panics on boot - it seems that if you recompile the kernel and change something this might go away.  An update causes the wifi drivers to disappear and the system to think that it is a single core 386 instead of using the SMP 686 one - I think that this stems from needing to use lilo instead of grub and is fixable.  Over all, I think that in a little while, everything on this box will work perfectly but not right now.  If you want it to be easy and have everything "just work," I would probably go with the Compaq for the short-term.

---

### Post by cosine7 on 2006-08-04
> **martinbures said:**
> I have a 2Ghz Macbook.  I bought it with the express purpose of putting Linux on it.  OS X is alright, but I use Dapper on my Opteron desktop and like it and want to use the same thing on the new Apple hardware.  Problem is that it Dapper has not quite caught up with the Macbook hardware.  It takes a bit more work to install.  You can get everything working except for a few things fairly easily.  Those things are the advanced touchpad features - two-fingered scrolling like under OS X.  I haven't seen anyone saying that they got this working - correct me if I am wrong - PLEASE!  I would love to have this feature working.  iSight requires a little work to get working.  On my box, it does not seem to throttle the cpu down when it is not very busy - so, it gets much hotter running Dapper than it does running OS X.  You have to do a special install and use an efi hack refit to, as I understand it, emulate a legacy BIOS.  There are occasional kernel panics on boot - it seems that if you recompile the kernel and change something this might go away.  An update causes the wifi drivers to disappear and the system to think that it is a single core 386 instead of using the SMP 686 one - I think that this stems from needing to use lilo instead of grub and is fixable.  Over all, I think that in a little while, everything on this box will work perfectly but not right now.  If you want it to be easy and have everything "just work," I would probably go with the Compaq for the short-term.


Thanks martin,
Those where the type of things that i wondered about, give it time, i'm sure they will get it going soon. I might hunt for a g3 ibook or something...

---

### Post by manofsteel on 2006-08-05
I would search the hardware compat list to see which iBook dapper is best suited for.

---

### Post by cosine7 on 2006-08-05
> **manofsteel said:**
> I would search the hardware compat list to see which iBook dapper is best suited for.

wow, where is that?

---

### Post by manofsteel on 2006-08-05
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

[https://wiki.ubuntu.com/UbuntuOnMac](https://wiki.ubuntu.com/UbuntuOnMac)

just wanted to give those who are looking for some links other choices, but the bottom one is for you .

---

### Post by cosine7 on 2006-08-05
> **manofsteel said:**
> [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

[https://wiki.ubuntu.com/UbuntuOnMac](https://wiki.ubuntu.com/UbuntuOnMac)

just wanted to give those who are looking for some links other choices, but the bottom one is for you .
Thanks for that i also found this one
[https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz](https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz)
looks pretty well suported

---

### Post by manofsteel on 2006-08-06
thats nice, how did you get it to show you that much detail in terms of what it supports?

---

### Post by huygens on 2006-08-09
> **manofsteel said:**
> [...]how did you get it to show you that much detail in terms of what it supports?

You will probably be interested by this link: [https://wiki.ubuntu.com/LaptopTestingTeam/Apple_Macintosh](https://wiki.ubuntu.com/LaptopTestingTeam/Apple_Macintosh)

Huygens

---

### Post by cosine7 on 2006-08-09
> **manofsteel said:**
> thats nice, how did you get it to show you that much detail in terms of what it supports?

I just went to the wiki and searched for "ibook"

---

### Post by cosine7 on 2006-08-11
UPDATE
If anyone is intrested, i actually got a 12" G3 700 White iBook, which have just put Dapper on. Got for about the 1/4 of the price of the macbook. :D

---

