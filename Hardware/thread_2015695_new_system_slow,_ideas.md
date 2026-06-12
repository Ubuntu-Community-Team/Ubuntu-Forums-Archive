---
title: "new system slow, ideas?"
date: 2012-07-03
forum: Hardware
---

### Post by warriorfrog on 2012-07-03
I've had it with XP and decided to make a linux box out of an older  system (running 12.04).  I thought it would be faster but it's rather slow.  It could be  (I feel this is most likely) that the hardware is just old or that I've  done something wrong.  I'd like some opinions.  


Hardware:
Asus P4T533-C
P4 2.26ghz
1.5gb RDRAM
ATI Radeon 9800XT (I think this may be causing graphics to be slow because of driver issues)

---

### Post by papibe on 2012-07-03
Hi warriorfrog.

Ubuntu 12.04 won't run very snappy on that hardware. I would recommend taking a look at other distributions that are more suitable for your computer.

Within the Ubuntu family you have 2 options [Xubuntu]("http://xubuntu.org/") and [Lubuntu]("http://lubuntu.net/").

I personally would recommend Xubuntu. I'm running it on a very similar laptop and I'm very pleased.

I hope that points you in the right direction.
Regards.

EDIT: If you don't mind being a little behind, you may also try Ubuntu 10.04.

---

### Post by ahallubuntu on 2012-07-03
You're right, this hardware is never going to be fast with a modern version of Ubuntu.  But the CPU and RAM are very acceptable for a basic system. I've put Ubuntu on much slower machines with less RAM.

You may also be right about the graphics card driver, though I guess you have to tell us what you mean by "slow."  In what context?  What should be faster in your opinion?  Opening a window?  Viewing Youtube?

I would check "Additional Drivers" for a proprietary driver for the video card and install it if such a driver is available.

FYI, on a system old enough to have XP, hardware problems are possible especially with the hard drive.  Did you confirm the hard drive is OK?  (Check it's S.M.A.R.T. status?)  Sometimes a failing hard drive could still be usable but slow the system way down.

Did you leave XP on it and dual boot Ubuntu or did you erase XP completely and have only Ubuntu on your hard drive?

---

### Post by QIII on 2012-07-03
Your card is unsupported by the current ATI drivers.  It is a legacy card and the legacy driver will not work with versions of X server post 2008.

If anyone suggests attempting to install the proprietary driver, don't.

You won't find a suggestion in Additional Drivers for that card.

The open source Radeon driver (which you are using by default) is very good these days.  You may even get good 3D support.

I second the Xubuntu suggestion.

---

### Post by warriorfrog on 2012-07-03
Papibe:  Interesting.  Will Xubuntu run normal Ubuntu applications?  

ahallubuntu:  I formatted the hard drive and install 12.04.  The system lists an error instead of a graphics driver so I assume it's not using one.  Firefox is slow, moving windows is sometimes choppy.  Response feels slow.  Running commands and the like in a terminal is just fine though.  I don't think there is a proprietary driver for the 9800XT (it's and old card, but was TOTL at one time lol).  I think the hard drive is OK, but I'll check it.  The system is old though.  I think I built it in 2001!

---

### Post by papibe on 2012-07-03
> **warriorfrog said:**
> Papibe:  Interesting.  Will Xubuntu run normal Ubuntu applications? 

Yes.

---

