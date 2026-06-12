---
title: "Help on Sapphire ATI HD 3850 AGP"
date: 2010-04-01
forum: Hardware
---

### Post by xandones on 2010-04-01
Hi!
I have a Sapphire ATI HD 3850 AGP and I couldn't make it work on Ubuntu. It "works" without the drive, but if I install or update the system, the screen crashes without any possible recovery. Is there any way to make it work on Ubuntu?

---

### Post by WSmart on 2010-04-03
Looks like support was dropped after Ubuntu 8.10.  With 8.10 you should be able to install it from the Hardware Driver program in the System>Administration menu.  

Also the open source driver is close to supporting 3D with this.  If you install Ubuntu 10.04 and update to the latest radeonhd version, it might work.  [http://www.x.org/wiki/radeonhd:INSTALL](http://www.x.org/wiki/radeonhd:INSTALL) 

I've got a CRT and I can't get that to work with Linux, with a DVI to VGA adapter, even with an older card that has both and works fine from the VGA.  But the 8.10 install and the 10.04 both looked promising, didn't totally crash and looked like I just had the DVI to CRT issue.  .

Love ot hear if you have any success.  

Thanks all.

Edit:   I had to do F4 and select safe graphics mode to get the liveCD to boot.  The install worked fine from there.  Found that via bug report.

---

### Post by CorsairTrumpet on 2010-06-18
I'm having a similar issue, I can't get my card to work beyond basic functions.  fglrx is only 300 or below and that just doesn't seem right.

MOBO: ASUS p4p800 se
4gig Corsair
p4 3.0 oc to 3.2
ATI 3850 HD AGP.

thanks for any input.

---

### Post by sastusbulbas on 2010-07-11
Have any of you guys solved these issues? 

Using an HIS IceQ HD3850 AGP myself.

---

### Post by WSmart on 2010-07-11
You can try 8.10 or the open source driver.   

I bet the open source driver has 3D support now, but it might not automatically install yet.  Could be they will have the same problems the AMD development team did and give up on it too.  I don't know if the AMD development team has given up on it, entirely, but it be looking that way.  That would mean AMD effectively dropped support for all AGP cards.  They officially dropped support for the older cards after 7.10 Ubuntu.

One issue with 8.10, support for that will be dropping and then you won't be able to get the disc/image or updates, I believe, fyi.    

Love to hear if this works for anyone. 

Thanks

---

### Post by Centx on 2010-12-04
I know this thread is old, but just wanted to mention that my Sapphire Radeon 3850 AGP just started working with fglrx (from official repos) under ubuntu 10.10 today. I vaguely remember that I tried installing fglrx when I first installed 10.10, and that it didn't work back then.

Just in case any of you guys still have problems, sitting on older ubuntus, or if someone googles and finds this post (like I did just now).

cheers!

---

