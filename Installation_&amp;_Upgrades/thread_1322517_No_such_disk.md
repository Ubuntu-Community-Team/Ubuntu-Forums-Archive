---
title: "No such disk"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by brokenjames on 2009-11-11
I kept receiving the grub error like every one else and this is how I fixed it. I was installing the new version of Ubuntu to two of my computers at the same time. One of them worked the other kept giving me the NO such disk error. I decided to see it if it was hardware and I switched the hardrives and all of a sudden it started booting up correctly on both of them. Now this dosnt make any sense untill I noticed that one hard drive 20g was a lot smaller and working on both. The larger hardrive wasnt working on the older machine. This made no sense to me at all so I switched out to a different power supply on the computer that was giving me problems and I could boot both hard drives no problem. 

Long story short I dont know much about how the computers boot up but I don't think the hardrives spin fast enough and the grub times out/just throws its hands up and walks away to windows 7. :(

---

### Post by Mark Phelps on 2009-11-11
> **brokenjames said:**
>  ...Long story short I dont know much about how the computers boot up ...

That's correct -- you don't. GRUB is not going to time out due simply to hard drive spinup. If anything, the newer larger drivers tend to have faster rotation speeds and shorter spinup than the older smaller drives.

What's more likely the case, since you say the second PSU (Power Supply Unit) worked, is that one of the power leads (known as rails) on the other PSU was faulty or the connection to the plug was intermittent, resulting the in the drive not getting enough power to be reliable.

---

