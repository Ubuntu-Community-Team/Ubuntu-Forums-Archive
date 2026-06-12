---
title: "Belkin F5D8053 usb N wireless help"
date: 2012-04-18
forum: Hardware
---

### Post by _Sweep_ on 2012-04-18
Hello all I have a F5D8053 usb N wireless stick that I am trying to get setup.  I found this:  [https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053) .

I am at the part that says "Now you need to go to the directory where you downloaded the drivers and run it. $ wine f5d8053v3_ww_02.0.0.04_w2.exe"  but I can get it to work and it says wine: cannot find L"C:\\windows\\system32\\f5d8053v3_ww_02.0.0.04_w2.exe.

I have messed with this for an hour or two and can't figure it out.  I am on the latest version of ubuntu and it is the 64bit version.  

I am a newbie and this is probably a pretty easy thing but any help would be appreciated.

Thanks

---

### Post by ahallubuntu on 2012-04-18
If you google for "F5D8053 ubuntu" you'll find lots of past posts (many on this forum) about this troublesome wireless adapter.  Apparently, over various versions of Ubuntu support for the adapter changes - kind of works, get flaky, then breaks again...

You can do your own googling and look for recent threads that might apply to Ubuntu 11.10 (assuming that's the version you have installed).  Try some of the solutions people have tried there.  (It sounds like using the Windows driver with Ndiswrapper is not the preferred solution these days though).

The sad fact is, some hardware works really well with Linux and other hardware is poorly supported and it can be a pain to get it working in Ubuntu.  This is especially true with wireless cards.  That's why I try to look for wireless cards that seem to have the best support.  I always opt for Intel (internal) wireless cards in my laptops because they seem supported out of the box and cause the least trouble.  I've found some Realtek-based USB wireless dongles that seem to work pretty well once I install a driver.  It's kind of hit or miss, though!

---

### Post by _Sweep_ on 2012-04-19
Ok thanks.  Tried a couple other threads that people had but with no luck.  Guess I will have to install windows xp for my mom in order to get it to work, shrug.

---

