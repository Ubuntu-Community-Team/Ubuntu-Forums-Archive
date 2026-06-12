---
title: "Ati Radeon X800 Support under 9.04, fglrx, upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by ales on 2009-04-24
Hello,


I just wanted to upgrade to 9.04 from 8.10, but the system warned me, that my Radeon X800 is not supported under 9.04 / no fglrx driver.
On ATI pages, there is written, that users with older chips should use 9.3 driver, because 9.4 is not supporting older cards anymore. 
So can I upgrade and use fglrx driver from ati 9.3 under 9.04, or will it not work under 9.04?

It is not clear if there is no prprietary driver suport, or if the 9.04 will accept the 9.3 drive from ATI and work with it?

Thanks for any comments.

Ales

---

### Post by Hixxy on 2009-06-13
I am also trying to get my X800 working on 9.04 but when I install the fgxlr(?) driver my screen looks all messed up and the computer locks up.

---

### Post by ales on 2009-06-13
I gave up. Just now use open drivers, of course no games running. I play under XP Enemy Territory, Smoking Guns,.. simply all I played before under Liinux, ITS UNBLIVABLE THAT THEY FORCED ME TO USE XP BECAUSE OF THIS. It was a big mistake...

---

### Post by sir KitKat on 2009-06-23
I was wondering. Has any one found a fix or will there be a fix in the future?

The only solutions now are:
[s]- Stay on Ubuntu 8.10 and wait for the solution to be found[/s]
- Buy new Grafix Card
- Turn to Win XP/Vista

Someone?

grtz,
sir KitKat

---

### Post by Mark Phelps on 2009-06-23
Hey folks.  Perhaps you should both TRY searching the forums on this topic before posting.  All your questions have been answered ... again and again and again.

But ... since you won't do that, here are the answers (again):
1) AMD/ATI dropped support for all but the newer "HD" cards with Catalyst 9.4 and newer
2) Only Catalyst 9.3 and older work with the older cards -- and these won't run in Ubuntu 9.04 due to incompatibility with the version of Xorg.
3) AMD/ATI has not indicated ANY plans to change their current direction.

So, as has been said repeatedly, if you have one of the older ATI cards, you either have to be content with using the open source drivers, or you will have to switch to a non-ATI-chipset card.

---

### Post by Richard951 on 2010-07-09
This is Exactly why I am still using windows.  I thought 8.04 was great and little did I know, upgrading to 9.10 without driver support for my x800 GTO.  I must credit windows 7 for it's legacy drivers support by porting xp drivers.  I still like ubuntu.  I hope ubuntu developers step up without much relying on third party drivers.

---

### Post by Mark Phelps on 2010-07-09
> **Richard951 said:**
> ... I must credit windows 7 for it's legacy drivers support by porting xp drivers.  I still like ubuntu.  I hope ubuntu developers step up without much relying on third party drivers.

I'm using one of the Legacy ATI cards, in Ubuntu and Win7 -- and in all fairness, the credit (or blame) really needs to go to AMD/ATI.  They have dropped Linux support for the Legacy cards, but they continue to provide MS Windows support.

You should check with their website for Legacy drivers.  The latest one that I know of is Catalyst 10.3 (or is it 10.2?), anyway, they do keep their drivers somewhat up to date for MS Windows.

When you do the driver download, make sure the filename include "legacy" in it, otherwise, you'll be downloading the other driver, and it will NOT work with your Legacy card.

---

