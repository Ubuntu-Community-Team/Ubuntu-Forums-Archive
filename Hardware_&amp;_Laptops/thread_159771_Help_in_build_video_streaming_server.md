---
title: "Help in build video streaming server"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by alea on 2006-04-13
Hello, 



First a little background: 

I have a lan formed of a G4 with MacOSX and a Satellite receiver (a Dreambox 7000 to be precise) with a 100Mbit/s ethernet card running a striped down and customized version of Linux. The Dreambox is capable of mounting nfs-shares and play the movies stored on the shares (It can also mount cifs-shares). 

At the moment I am sharing a harddisk in my G4 and mounting it on the Dreambox. 



What do I want to do: 

My intention now is to buy a cheap PC, where I can store several harddisks that will be available by sharing to the Dreambox. 

- After the first configuration, I want the pc to remain without keyboard and monitor; it should only be connected to the lan (and the power, of course). All maintainance should be made remotly through the lan from my Mac. I have heard about vnc... 

- When there is no nfs-streaming activity, the pc should use the less energy possible; I am thinking on suspend to disk; maybe even a complete poweroff if possible  

- The pc should be able to start (wake up) by a wakeonlan packet. (The dreambox is capable to send wol on demand). 

- To run the system, I would like to use a GNU/Linux distribution; as I read that ubuntu is quite user-friendly, I suppose it will be a version of ubuntu, probably dapper, as I read that it will be shipped with suspend to disk included. 



A few words about my computer knowledge: 

Right away, let me tell you that I am not a pro and that I have never used a GNU/Linux distribution before. However, I am able to download sources from a cvs and compile them for my mac if I have a howto (for example I recently compiled clamav88.1). Moreover, I also played a bit with fink, a system to port free software to MacOSX. Consequently, I suppose that I will also be able to work with Ubuntu, if I will not have to address issues of not supported hardware and the like... 


Could you please tell me if it will be possible to achieve my aim with the following hardware and what Ubuntu-version I should use? 

Medium Tower ATX Antec SLK 3700 BQL noir
Motherboard AsRock 775i65GV Socket LGA 775
Processor Celeron 2,8Ghz D Socket LGA775
Memory 512MB DDR 400Mhz KingMax SuperRam

When I read the bios-section of the manual of the motherboard, it only speaks about suspend to ram; will ubuntu override it and also allow a suspend to disk?  

Are there any issue I will get with that hardware?

I will be grateful for any help and comment about my project. 


Thanks in advance. 

alea

---

