---
title: "Unexpected System Speedup - Ubuntu 8.04.2, Kernel 2.6.24-23"
date: 2009-01-19
forum: Hardware
---

### Post by SuperMike on 2009-01-19
Hey, Ubuntu. I don't know how you did it, but I'm seeing a slight performance improvement in my Ubuntu 8.04 workstation now that I'm on Kernel 2.6.24-23. I also noticed that my nVidia driver was updated, so perhaps that's the help as well. 

However, the boot time is still slow on my Acer Extensa 4420 laptop. The slowness appears to be, in order of my perception:

1. PostgreSQL service (which I need for my work). Note the MySQL service just loads super fast and moves on, so it's not even on this list.

2. Virtualbox drivers (again, needed for my work, for testing browsers). This is only slightly slow because it has to load two drivers.

3. Wireless Ethernet -- must be waiting for an address? It's only slightly slow.

It takes me over 70 seconds to boot and get to a desktop application menu that is responsive.

But, anyway, besides the boot time, I'm faster, so I'm happy.

---

