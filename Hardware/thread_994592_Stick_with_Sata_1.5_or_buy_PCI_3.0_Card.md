---
title: "Stick with Sata 1.5 or buy PCI 3.0 Card"
date: 2008-11-26
forum: Hardware
---

### Post by KnavishClout on 2008-11-26
Hello all.  I'm about to purchase a hard drive to go into a slightly aged PC that only has onboard Sata 1.5 ports.  This hard drive will be used to store video captured by a TV Tuner (being ported from an older Video Camera).  

The question is whether I shold just stick with the 1.5 ports that are onboard or should I spend the extra $15 to get a Sata 3.0 carrd that would plug into a standard PCI port.  The $15 is nominal for me if I would notice a difference in performance.  What do you think?

---

### Post by markbuntu on 2008-11-26
The 3.0 is a maximum possible, it is no guarantee you will get that. I am not sure a pci bus will even support it realistically since many devices share the bus. 

I used one of those cards for a while and it had its own bios that would load after the mobo bios which sort of remapped the sata drives causing weird grub errors but if you are just using it for storage drives that should not be a problem for you.

Anyway, I did not notice much difference in performance. If you were going to add drives and had no more sata plugs I would say go ahead and do it but i don't think you will see a noticeable difference by just moving drives for what you want to do. Most of the large drives are buffered anyway these days so the real bottleneck for performance is the bus and cpu sharing.

---

### Post by tommcd on 2008-11-26
If it is an old PC, I would think that the CPU and video card would potentially be more significant limiting factors on video performance than the sata 1.5 vs 3.0 ports. I really don't think you would notice much difference. My Asus K8N motherboard (nvidia nforce 3 chipset) only has sata 1.5 and I think it works just fine.

Also, the pci bus could potentially be a limiting factor also with the sata card.

---

### Post by KnavishClout on 2008-11-26
I can't believe I forgot to add the specs!  The PC is an AMD Athalon 64 running Ubuntu (Hardy Heron 32bit) with 2GB DDR2 Ram.  The primary hard drive is a 15000 RPM SCSI Hard Drive but it's only about 10-15GB.  That's why I need extra storage for my home movies.  

Given what I've heard so far, I suppose I'll stick with the onboard 1.5's, but if anyone has anything else to add, please go on!

---

### Post by markbuntu on 2008-11-27
I am running both 32 bit and 64 bit Hardy on my machine which is very similar to yours. I just replaced my mobo and cpu, the old one had a amd 64 3800+ single cpu, the new one has a AMD 64 6000+ X2 cpu 2GB DDR2 ram with 4 hard drives, 2 320GB, 1 160GB and 1 250GB. 

I also have a ATI HD36501GB PCI Express graphics card. That made a huge difference in cpu loading for graphics rendering with both mobos so you might consider a plug in graphics card with 512MB or more ram if you are still using the on board one. That will take a lot of the rendering load off the cpu bus and would speed things up considerably in that department.

If you are getting another hd, all the new ones can do 1.5 and 3.0 so don't worry about that. Just get the biggest one you can afford and use it just for media storage and mount it as /something in your home directory. You can keep the OS on the one you have now. This will avoid any possible trouble with losing data when you change OS or do any hardware upgrades in the future.

---

