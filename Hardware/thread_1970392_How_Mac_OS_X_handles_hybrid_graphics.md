---
title: "How Mac OS X handles hybrid graphics"
date: 2012-05-01
forum: Hardware
---

### Post by suryak on 2012-05-01
As Linux is not really good at switching graphics (dedicated to in-build). I wonder how mac os x is handling this issue??

Do, mac users also use switcheroo and all the **** (these even doesn't switch on run time)

---

### Post by buzzingrobot on 2012-05-01
> **suryak said:**
> As Linux is not really good at switching graphics (dedicated to in-build). I wonder how mac os x is handling this issue??

Do, mac users also use switcheroo and all the **** (these even doesn't switch on run time)

You can tell a MacBook to always use the GPU, or you can tell it to use the onboard chip and automatically switch to the GPU when needed.

---

### Post by suryak on 2012-05-01
Then why it doesn't possible in Linux distro's. Even OS X is from UNIX family!!!

---

### Post by 2F4U on 2012-05-01
> **suryak said:**
> Then why it doesn't possible in Linux distro's. Even OS X is from UNIX family!!!

OSX is a proprietary system running on a limited selection of hardware, which is hand-picked by Apple (hardware vendors develop according to the requirements of Apple and provide Apple with any internal information that is necessary). It is no wonder that it works. Linux, on the other hand, often doesn't get much information and support by hardware vendors, developers often have to guess how the hardware works,  and Linux has to work on a broad variety of hardware.

---

### Post by buzzingrobot on 2012-05-01
> **suryak said:**
> Then why it doesn't possible in Linux distro's. Even OS X is from UNIX family!!!

It also really has nothing to do with Unix. Unix itself knows nothing about graphics and GUI's and mice and such. Anything that burrows deep into hardware has to be coded specifically to deal with the piece of hardware.  Take all that stuff away and you'd still have text-based Unix, as it was originally developed. As long it it could talk to green-screen monitors, you were good to go.

---

### Post by suryak on 2012-05-01
> **buzzingrobot said:**
> It also really has nothing to do with Unix. Unix itself knows nothing about graphics and GUI's and mice and such. 

Well, if that's the case, the switching of hybrid graphics is only in "ubuntu"??

---

### Post by buzzingrobot on 2012-05-01
> **suryak said:**
> Well, if that's the case, the switching of hybrid graphics is only in "ubuntu"??

No. If a Linux driver is written to deal with "X" hardware from "Y" vendor it's available to all.

The issue is this:  Linux, in particular, the kernel, needs to support a vast array of hardware from thousands of different vendors. Those products are made to sell into the Windows market.  Their vendors have an incentive to write code to make sure their products work in Windows. Microsoft has an incentive to ensure that new Windows releases don't break old code. 

That doesn't happen in Linux, usually. Linux developers are on their own to figure out how to interface with hardware.  Vendors like AMD and Nvidia who release open source drivers for their proprietary products are exceptions. Linux developers, frankly, have no  idea if their code will work with every possible piece of hardware that's out there.  They can't.

That said, things are very much better than they were several years ago, when getting something like a wifi card to work was a real battle.

Apple has a great advantage because it controls both the hardware and the software in its products. it works with a very small set of hardware and doesn't worry about anyone else's hardware.  While the hardware in Apple's is actually pretty much off-the-shelf, not custom, stuff, I wouldn't be surprised if hardware vendors tweaked their products at Apple's behest.

There are Hackintosh hobbyists who run OS X on non-Apple hardware and they have at least as many hardware issues as Linux users.

---

