---
title: "how much ram can 32 bit ubuntu see"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by ljonesj on 2008-03-31
i heard windows 32bit if you have 4gb of ram only sees 3.5gb of it whats the limit of ubuntu 32bit

---

### Post by ToySouljah on 2008-03-31
When I installed the 32-bit version the system only recognized 2.7GB, after switching to 64-bit the system shows 3.9 (4GB).

---

### Post by LaRoza on 2008-03-31
> **ljonesj said:**
> i heard windows 32bit if you have 4gb of ram only sees 3.5gb of it whats the limit of ubuntu 32bit

It is the limit of the hardware, a 32 bit processer can't address more RAM than it can.

---

### Post by stefangr1 on 2008-03-31
Thats right, the default 32bit kernel supports up to 4GiB, but some of that might be reserved depending on the hardware so that the real amount of RAM that can be used is lower. It is theoretically possible to recompile a 32 bit kernel that supports over 4GiB, but thats for the experts.

---

### Post by ljonesj on 2008-03-31
no worries for me i have a dual core amd 3ghz

---

### Post by sdennie on 2008-03-31
It's not really a hardware limitaiton but more the fact that the software is directing the hardware to behave in a certain way.  It's not possible to see 4G of RAM using a "pure" 32-bit OS even if you are running it on a 64-bit capable machine because, as stefangr1 said, the OS has to map some of the hardware into those 32-bits and so it will always overshadow some of the RAM.  Using a 64-bit OS, I think the same problem exists but, you won't see it until you have about 16 exabytes of RAM (which is a lot).

You can however see more than 4G of RAM on a 32-bit OS if you use a kernel that supports PAE, which essentially makes the kernel 36-bit (but I believe still limits you to 2G of RAM per process).  On Ubuntu, I believe that the 32-bit server kernel has PAE enabled but, I'm not sure if it's tuned well to run on a desktop or if it has the same number of drivers as the default kernel.  You could try it out by doing:

```

sudo apt-get install linux-image-server

```

And then making sure you select it at boot time from the grub boot menu.  

The other option, if you really want to use a 32-bit OS with 4GB or more of RAM, is to build a custom kernel with PAE enabled.

Of course, you could also just use the 64-bit version of Ubuntu and everything should just work...

---

