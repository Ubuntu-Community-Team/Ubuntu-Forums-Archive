---
title: "Looking for lowcost sata controller working out of the box in feisty and beyond"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by frafu on 2007-04-16
Hello, 

I am looking for a lowcost sata controller that works out of the box in feisty and beyond. 

It should have at least connectors for 4 sata drives. 

It does not need to offer hardware RAID. 

I have the intention to plug it into a pci connector of my ASRock 775i65GV motherboard that has a Celeron D CPU. 

If you need more information, please tell me so. 

Thanks in advance for any suggestion. 

Francesco

---

### Post by frafu on 2007-04-17
bump

---

### Post by frafu on 2007-04-18
I think that I will buy the [ST Lab A-223]("http://www.st-lab.com/products-1.asp"), that should cost around 30$.

It has a Silicon Image 3114 chipset and if I am not doing a mistake, it should be natively supported by the last kernels. 

Can anybody please confirm? 

Thanks in advance.

---

### Post by frafu on 2007-04-28
I can confirm that it works out of the box on my 775i65gv motherboard with a celeron d processor and Ubuntu 7.04.

Have a nice day.

---

### Post by grss1982 on 2007-06-15
Speaking of the 775i65gv, does this thing work with Ubuntu out of the box? especially the built-in VGA, LAN & Sound? :popcorn:

---

### Post by frafu on 2007-06-16
Hello, 

I can confirm that the vga and that the lan (with wol) work out of the box. 

Concerning the sound, I think that it works too because the volume slider is available on the upper panel. But I cannot confirm it for sure, because there are no speakers connected to it and I am using it remotely. 

Finally, I don't know whether it was due to the motherboard or the sata-pci card, but there are a few problems with the 2.6.20 kernel. The last kernel update fixed the heaviest problem, but there still are little issues. Reading around, I discovered that there are many people with similar problems. 
[Long boot time.]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118803")

[Link to all the bugs that I filed.]("https://bugs.launchpad.net/~francesco-fumanti/")

Francesco

---

