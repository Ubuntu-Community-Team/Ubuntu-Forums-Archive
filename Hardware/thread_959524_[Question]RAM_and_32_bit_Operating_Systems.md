---
title: "[Question]RAM and 32 bit Operating Systems"
date: 2008-10-26
forum: Hardware
---

### Post by ChompTheMan on 2008-10-26
I recently purchased 2 sticks of 2GB RAM and added them to my computer along with my already installed 1GB and 512MB sticks of RAM.  To make a long story short, I discovered that the BIOS shows 5632MB of RAM while Windows and Kubuntu only show 3.25GB and 3.21GB of RAM.  After a bit of research I discovered that 32 bit operating systems can only display(use?) up to 4GB, usually showing between 3.2 and 3.5GB depending on how much your video card takes up.

Now, what I am a little confused about, and have not been able to find a clear answer on, is whether or not 32 bit operating systems will use all of my installed RAM or just up to 4GB.  Some answers say yes, some no.  Are there any experts here who can answer my question in a newb friendly manner?

---

### Post by Faryshta on 2008-10-26
That myth is true.

Since you have a 32 bits system you can only use on top 2^32 bytes of ram, which is 4GB. And If you count the swap and the memory on the video card you are wasting many ram there.

The solution is to upgrade to 64 system bits if you want to use that much ram but honestly I think is pointless since you are not launching space rockets or calculating mersene primes.

2GB or ram should be more than enough, also if you have a video card their ram also counts and the swap partition so.

---

### Post by cariboo on 2008-10-26
You  can install the 32bit server kernel to access all your memory. Search synaptic for linux-image-2.6.xx-server, where xx is your kernel version. It should work with no problem.

Jim

---

### Post by OutOfReach on 2008-10-26
The server kernel can be used to use all of your installed memory.
I think you can also recompile a normal kernel to use PAE, which will be able to make use of all of your memory.

---

### Post by Kevbert on 2008-10-26
You can use all your memory if you have [[COLOR="Red"]PAE[/COLOR]]("http://en.wikipedia.org/wiki/Physical_Address_Extension") support which I believe comes with the server versions of 32 bit Ubuntu and in theory you should be able to address up to 64Gb RAM.

---

