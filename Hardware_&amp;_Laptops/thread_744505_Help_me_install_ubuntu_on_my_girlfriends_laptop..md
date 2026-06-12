---
title: "Help me install ubuntu on my girlfriends laptop."
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-04-03
My girlfriend has an HP pavilion dv6000 running Windows Vista. The machine is new and has decent specs but Vista runs slower then molasses on it. Today she picked up my Ubuntu laptop and was blown away by how fast everything was. Now she wants me to install Ubuntu on her laptop. 

I popped in my live CD and booted it up. On the first two tries the machine froze during boot up. The third time around I tried starting in graphical safe mode and that got me to a desktop. I noticed the machine detected no wifi networks. I started up the install and plugged along until I got to the partitioning stage. There I found that neither the installer partitioner or Gparted could resize her Vista partition. It was locked at full size. How do I repartition her disk to make room for an Ubuntu boot?

Also, does anyone know how hard it is to get wireless internet working on this machine?

---

### Post by Sef on 2008-04-03
> There I found that neither the installer partitioner or Gparted could resize her Vista partition.

Use Vista's partitioner to shrink the partition.

---

### Post by JaggedOne on 2008-04-03
Ahh that worked. Why are Vista partitions so muddled that only Vista's partitioner can make sense of it?

Anyway, my two other questions are this:

1. How hard is it to set up wifi on this laptop? 

2. Is the fact that it only booted off the live CD in safe mode going to cause problems? If so how do I fix them.

Ill post more when I get further along in the install.

---

### Post by ljonesj on 2008-04-03
what type of graphics card does it have

---

### Post by pseudo-random on 2008-04-03
Wifi is easy. You have the choice of the network GUI or wpa_supplicant from the command line (search the forums)
You only have to configure it once then its done.

---

