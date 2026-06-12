---
title: "Raspberry PI Users hardware requirements for Ubuntu 24.04"
date: 2024-04-09
forum: Hardware
---

### Post by Joe_Linux on 2024-04-09
Is their a sub-forum for users of Ubuntu on a Raspberry PI 4 or 5 ? Also what are the hardware requirements for a Raspberry PI 4 in Ubuntu 24.04 (out on 04/25/24)

                                                                                                                               Thanks

---

### Post by Joe_Linux on 2024-04-17
Bump

---

### Post by TheFu on 2024-04-18
I didn't look.  Raspberry Pi SBCs come in only a very few configurations, so I'd expect the 4GB RAM and higher versions would work fine.  1GB RAM versions, not so much, but it depends on the DE used, as always.  Gnome is bloated, so it will need more CPU, more RAM, and more storage.  KDE is less bloated, so it will need less of each.  Ubuntu-Mate/XFCE/Lubuntu are lighter releases, so those will need even less than KDE/Kubuntu.  If you use a server version, not a desktop, cut the requirements by 50%.

But until it is released, we really don't know.  Nobody here works for Canonical.  You can google for the answers just as well as we can.
[https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi) was found.  The 23.10 requirements/certification is about the best we have today.
**_Minimum 4GBs of RAM required_** is the requirement for 23.10 on a Pi4.

[https://ubuntu.com/certified?q=&vendor=Raspberry+Pi+Foundation](https://ubuntu.com/certified?q=&vendor=Raspberry+Pi+Foundation)  Looks like the 1G Pi4 has an image for 22.04.  I hope it isn't a desktop. I think any GUI would be painful on that little RAM.  I'm finding the Canonical website to be too much trouble to use - constantly asking for cookies to be relaxed.

If you'd like paid Canonical support, [https://ubuntu.com/download/iot](https://ubuntu.com/download/iot) says that 
> Ubuntu applications depend on a wide range of kernel features such as security modules, filesystems and container primitives. Ensure that your device kernel meets Ubuntu application expectations with a Canonical built custom kernel. Enablement fees vary from $25k to $200k as a one-time charge, depending on the particular board or chipset. Canonical delivers a custom kernel matching a standard Ubuntu LTS release, or interim release with a path to the next LTS.
or
> For an annual charge of $25k, Canonical will perform continuous security maintenance and testing on your board. When a security issue is fixed in Ubuntu, the fix will be tested on your board. These security updates will be published to the snap store for use on your device.

So you have some paid support options available.

---

