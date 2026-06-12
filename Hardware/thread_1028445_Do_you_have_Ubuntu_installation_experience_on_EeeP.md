---
title: "Do you have Ubuntu installation experience on EeePC?"
date: 2009-01-02
forum: Hardware
---

### Post by PryGuy on 2009-01-02
Good day! I have EeePC and I tried to install Intrepid on it today (it came with Windows). Installation went smooth but I have two main problems:

1. System does not turn off properly after shut down, it has the power light on and I can't turn it on after that, have to re-insert battery to make it operational again.
2. Wi-Fi does not work properly, it loads the Atheros proprietary driver but I don't see the ath0 interface up when I ifconfig. I can't see any wireless networks as a result.

I know, you'll recommend me EeeXubuntu or other special distro, but is there a way to ovveride these problems? Thank you!

---

### Post by snowpine on 2009-01-02
Hi PryGuy,
There are several methods to get Ubuntu working on the eee pc; some good threads here and also over at forum.eeeuser.com. 

Personally, this is how I got Ubuntu Intrepid working on my eee 900ha: [http://array.org/ubuntu/setup-intrepid.html](http://array.org/ubuntu/setup-intrepid.html)

Good luck!

---

### Post by handydan918 on 2009-01-04
I just install eeebuntu. Everything works as is, except for the sd card.

---

### Post by m_duck on 2009-01-04
I've got Ubuntu Intrepid installed on my eeePC 1000. I just installed Intrepid, then the array.org kernel that snowpine mentioned (the lean one at present, I've had no problems so far). That sorted out wireless and stuff for me (though the 1000 has a Ralink wireless card, not an atheros one so can't be sure that will work in your case).

A useful script to get various bits working, like the extra buttons etc is [here on the eee user forums]("http://forum.eeeuser.com/viewtopic.php?id=49081").

---

### Post by DonnieP on 2009-01-11
> **PryGuy said:**
> 
2. Wi-Fi does not work properly, it loads the Atheros proprietary driver but I don't see the ath0 interface up when I ifconfig. I can't see any wireless networks as a result.
I, too, use and recommend the Array kernel.  But before I discovered Array I got wireless working on my 900A by following these instructions:

"Installing ath5k driver on Ubuntu 8.10 Intrepid Ibex"
Located on this how-to:
[EeePC Fixes]("https://help.ubuntu.com/community/EeePC/Fixes")

---

