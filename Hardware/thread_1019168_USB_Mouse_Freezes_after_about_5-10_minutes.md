---
title: "USB Mouse Freezes after about 5-10 minutes"
date: 2008-12-22
forum: Hardware
---

### Post by neoncode on 2008-12-22
I've grabbed the Kubuntu 8.10 amd64 live cd to install over my existing 8.04 x86 installation. But, on the Live CD I've again noticed a problem that I had before. After a period of short use, my USB mouse will suddenly stop working. 

Now, I noticed this problem before when I was setting up 8.04 and I just ignored it and used a USB to PS/2 adapter to bypass this problem. But I'd much rather solve the root cause.

As for more detailed information, I have two USB mice. A Microsoft one and an apple Mighty Mouse. I was using the Microsoft one by default and it froze. So I stuck in the Apple and that worked just fine. At this point lsusb output a couple of Linux USB hubs (a 1.1 and 2.0 one, I presume those are normal) along with the names of both mice. But when I unplugged the Microsoft one, the apple remained working still but any attempt to run lsusb left the process in disk sleep. Simply re-plugging the Microsoft mouse into the same or any other USB port did nothing, it didn't pick it up and the mouse didn't light up ether. Plugging in any new USB devices does nothing. Dmesg also shows no obvious errors (apart from something about a segfault in konqueror)

So, what on earth is going on? I've seen a few threads like this. None have any solutions. although a few suggest disabling some of the BIOS settings, and that frequency scaling the CPU corrupted the USB devices. I don't remember the thread so can't link it.

---

