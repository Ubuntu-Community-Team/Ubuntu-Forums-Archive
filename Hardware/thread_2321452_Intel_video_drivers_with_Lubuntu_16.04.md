---
title: "Intel video drivers with Lubuntu 16.04"
date: 2016-04-22
forum: Hardware
---

### Post by Jam_Holtman on 2016-04-22
I found out that there is an issue with the Intel video drivers, at least certain video drivers in Lubuntu.
I have noticed this already with 4 different "older" which use the Intel graphics controller series 945 and graphics controller based on the N455 CPU. Please see screenshots
When booting from the live USB of Lubuntu 16.04 either 32 or 64 bit I get a flashing cursor after a while.
The machine seems to boot but then it stops with a black screen and a flashing cursor in the top left corner.
Xubuntu live USB works perfectly on these machines.
The only way I can get Lubuntu to work on these machines is with the nomodeset command, but then the graphics doesn't look good and I have no dual screen support anymore.

---

### Post by roler2 on 2016-04-23
Whew! I am glad someone else is having trouble! Appears to be a conflict issue with the Kernel. If Xubuntu works then I might try that. I posted about this in another thread regarding the i915 and 945 driver, the updated Kernel and 16.04 Lubuntu. I just don't have the best setup for Xubuntu as I think it runs with the KDE Desktop, is that correct? I like the LXDE Desktop. You will get a black screen because of the updated Kernel issues conflicting with certain Intel Drivers, such as the i915 or the 945. The 14.04 default Kernel works great with those specific Intel Video Drivers. Unfortunately, no Kernel released after that has worked correctly with certain specific Intel Drivers, especially if they are old.

---

### Post by vasa1 on 2016-04-23
> **roler2 said:**
> ... I just don't have the best setup for Xubuntu as I think it runs with the KDE Desktop, is that correct? ...
Xubuntu uses XFCE, not KDE.

See [http://xubuntu.org/](http://xubuntu.org/) for more.

BTW, I'm sorry to read that you're still having those hardware problems.

---

### Post by roler2 on 2016-04-25
oops sorry! I posted this on another thread. If you have any suggestions I would really appreciate any assistance.  

"The i915 does not appear to work with Lubuntu 16.04. I am able to get to the Choice Screen. However, after that, nothing except a flashing cursor in the upper left corner and a completely black screen. Happens both in Live Mode and after Hard Drive Installation. I am able to install the entire system on the Hard Drive. I just can't boot to any type of Desktop at all.

I was able to boot to Desktop with the Beta Versions of 16.04. The font rendering was horrible, but at least I got something.

With the final release, I get nothing but a flashing cursor and a completely black screen. No messages. Nothing. My thought is that the newest Kernel does not support the i915 at all, given at least the Beta Versions I was able to access the Desktop.

Is there anything I can do to see if I can at least access the Desktop?"

---

