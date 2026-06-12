---
title: "4gb wont show correctly"
date: 2009-05-01
forum: Hardware
---

### Post by brendanbbaker on 2009-05-01
I installed 4gb of ram to my laptop today but every time I try to type in "free -m" it always comes up 2913 total even though theres 4gb. I think that it would show a bit more. I installed that PEF or whatever thing but that didn't help at all. Any ideas on how to get it to atleast read 3300mb?

---

### Post by PurposeOfReason on 2009-05-01
If you're using 32bit, that is you're problem. 32bit can only read 3GB.

---

### Post by 00b00nt00 on 2009-05-01
32bit systems can only use up to a maximum of 4GB address space. Most of this space will be consumed by RAM, of course, but other devices in your system must also use this address space, which is why you don't see the full 4GB of RAM. The easiest solution would be to install the 64bit version of Ubuntu, but for the sake of compatibility, many users stick to 32bit and resign themselves to the fact that some of their memory will be wasted.

The choice is yours.

---

### Post by brendanbbaker on 2009-05-01
Well, I did have 64bit installed but it still came up "2913" with "free -m". When I press F2 at startup and go to the second menu it says I have 4028mb of available space. Any ideas why it doesn't read?

---

### Post by 00b00nt00 on 2009-05-03
Could be an incompatibility somewhere. Google your computer's hardware specs and also see if there is a BIOS update available.

---

### Post by jords on 2009-05-03
Also, check your motherboard specs. If it only supports 4gb of address space, the amount of ram you can use will be lower because of the space needed for graphics cards etc. Ie if you want to use the full 4gb of ram, you need a motherboard that supports at least 5-6 gb. This doesn't change weather you use a 32bit os or a 64bit os. (You also need a 64bit os to use over approx 3 gigs).

---

