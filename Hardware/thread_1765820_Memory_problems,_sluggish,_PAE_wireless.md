---
title: "Memory problems, sluggish, PAE wireless"
date: 2011-05-23
forum: Hardware
---

### Post by peragrate72 on 2011-05-23
I know other people have had problems like mine, but I think it might be a case by case thing.

I have a Dell D620, and it's great. I just upgraded my memory from 2gb 667mhz to 4gb. The problem is that it doesn't seem much faster at all. Today, it was even pretty sluggish. Like when I had only 2gb.  I ran free and this is what I got:

             total       used       free     shared    buffers     cached
Mem:       3346156    3253840      92316          0     301072    2050800
-/+ buffers/cache:     901968    2444188
Swap:       780280      18460     761820

A few things aren't right here. The 3.3gb should say 4gb. At the time of tunning free, I have almost nothing running. The browser, thunderbird, transmission, and gnote. I've already shut down most of the start up applications.

I looked around and found out about a PAE kernel. So I tried that, and spent two days trying to get my wifi working again. So I changed back to the generic kernel: 2.6.32-31-generic.

While the PAE was installed, I did run free again. The results were the same as above. I can't remember what by bios says, but I'll reboot and find out. If it doesn't report 4gb at 667hz, I'll come back here and update this post.

Does anyone have any ideas? I really don't want to mess around with the PAE kernel because I need my wireless for work.

Thanks in advance...

---

### Post by trozamon on 2011-05-23
I also have a D620 (I'm on it right now), and unfortunately 3.3 GB of RAM is the max it recognises due to motherboard limitations.

The processor you have could determine why the speed is staying the same; if you have the Core Duo, 2 GB vs 3.3 GB of RAM won't make a difference, but it'll make a slight, slight difference with the Core 2 Duo.

---

### Post by peragrate72 on 2011-05-24
Thanks for the reply. However, here's the information from the manual I downloaded at Dell:

Memory 

Memory module connector
two user-accessible SODIMM sockets

Memory module capacities
256 MB, 512 MB, 1 GB, and 2 GB

Memory type
533/667 DDRII SDRAM

Minimum memory
256 MB
NOTE: For some regions, the amount of minimum memory may differ.

Maximum memory
4 GB


So, even Dell states that the capacity of this machine is 4gb.

Anyone?

---

### Post by trozamon on 2011-05-24
Once again, do you have the Core Duo or the Core 2 Duo(the 2 is of great importance).

Also, check your BIOS - I'm 99% sure mine says I have 4 GB installed RAM, but only 3.3 GB usable RAM. In my case, the motherboard is the limiting factor, not the OS; Windows would cause you the same trouble.

---

### Post by peragrate72 on 2011-05-24
Core 2 Duo

The bios reports 4096mb of Ram, but says only 3.3 is available due to resources reserved for the system. That sounds like a lot for a linux system, but I'm not sure. There's no way to change memory settings in this bios.

Otherwise, I'm not sure what to say. I guess I'm stuck with it... but this is a great laptop none-the-less.

---

