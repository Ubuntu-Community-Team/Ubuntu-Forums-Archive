---
title: "RAM available, linux version"
date: 2011-03-21
forum: Hardware
---

### Post by iamthesgt on 2011-03-21
I have two questions. I looked around for both of them, but the answers I got didn't help me.
(1) Why do I only have half the RAM availible? Using the system load monitor in the upper right-hand corner, it identifies 2.9GB of RAM and 4 processor cores. I have 6GB of RAM and an Intel Core i3 processor (does the i3 use hyper-threading or something? Because I know it's actually a Dual-Core)
(2) Where can I find which version of ubuntu I am running (32- or 64-bit)? I tried uname -m and it said i686. On the system monitor, it says Kernel Linux 2.6.32-30-generic. Does this mean I am 32-bit? If so, can I upgrade to 64-bit without deleting all of the add-ons I've installed?

---

### Post by Yellow Pasque on 2011-03-21
You're running 32-bit. You can't upgrade to 64-bit without a clean install, though if you have a separate /home partition, you can keep a lot of your configuration.
Enabling PAE may be an option if you don't want to reinstall at this time. [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by Thund3rstruck on 2011-03-21
Ouch.. yea i686 tops out at 3GB of ram. You need a 64-bit Operating System to use that 6GB of ram.

---

### Post by cascade9 on 2011-03-21
> **Thund3rstruck said:**
> Ouch.. yea i686 tops out at 3GB of ram. You need a 64-bit Operating System to use that 6GB of ram.

No, you dont. PAE will let you go past the 3.something limit. But I'd rather reinstall and use 64bit not a PAE kernel  myself.

---

### Post by cmileto on 2011-03-21
Well if you want to use alot of that 6 gb ram at once you will see better performance with the 64bit kernel. If you rarely max out the current ram then using the pae option will let you access the ram just fine but not as efficently.

---

