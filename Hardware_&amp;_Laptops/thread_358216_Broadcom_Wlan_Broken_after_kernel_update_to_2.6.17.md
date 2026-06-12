---
title: "Broadcom Wlan Broken after kernel update to 2.6.17-11!"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by TFrog on 2007-02-10
I'm truly amazed at this latest kernel update.  I expected to have to recompile my ATI proprietary drivers for the new kernel to get max 3D speed.  However, I was truly annoyed when I had to go back and download the latest ndiswrapper source code and still not able to get my wireless to connect with any driver I used to install via ndiswrapper :(  Oh, it did connect for a bit yesterday but now it won't connect at all with 2.6.17-11 kernel.  Funny thing is it won't even connect on an unsecure (no WPA or WEP encryption) network.   I REFUSE TO USE THE NATIVE DRIVER AND BE RELEGATED TO WIRELESS "B" STANDARDS ON A WIRELESS "G" DEVICE!  Nor will I use the far outdated ndiswrapper out of the repositories that some are saying may or may not work.  For now I'm making this post from 2.6.17-10 kernel.  At least even with the latest ndiswrapper from source compiled it works still.  I'm curious to know just how many others are having the same issues with Broadcom or any other wifi card and ndiswrapper.  Any?

---

### Post by Shatrat on 2007-02-10
Generally speaking, anything that you have to compile yourself which includes the linux kernel headers is going to have to be recompiled if you change the kernel and headers.
I know that for video drivers you need to recompile the interface shim when you change kernels.
You dont have to redo any of the process to set it up, I suspect its simiar with ndiswrapper, although I am not too familiar with it having only used it once.

---

### Post by TFrog on 2007-02-12
It's quite possibly true for ndiswrapper.  Just to update this.  Ndiswrapper works with the new kernel but drivers are unstable.  I'm using KDE 3.5.6 and signal strengths are not reporting as they did in the previous kernel and the drivers as I said earlier are unstable with the latest kernel and latest ndiswrapper.  I use PyWireless for monitoring the network and even it's signal strength shows a decided bad reading on networks with known capabilities under the prior kernel.  That is if and when the wireless connects.

---

### Post by TFrog on 2007-02-12
Further update!  It seems for some reason the old windows driver was held in memory even after doing ndiswrapper -e command after disabling the wireless.  upon rebooting and reloading the most current driver for windows I rebooted again.  This time everything works as expected.  Well almost.  With multiple open networks knetworkmanger has a tendency to be confused as to which to connect to.  That's to be expected though.  This thread may now be closed.

---

