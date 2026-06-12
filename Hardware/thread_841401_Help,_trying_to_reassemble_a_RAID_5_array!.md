---
title: "Help, trying to reassemble a RAID 5 array!"
date: 2008-06-26
forum: Hardware
---

### Post by porkbird on 2008-06-26
Hello All, 

Okay, I have a rather complicated problem that may or may not even be solvable. But here is the brunt of it. I have an old server that I need to get up and running again. Basically it is a 12 bay server with an SR-71 motherboard if that helps anyone, with a 3ware Escalade 8000 series controller. The server was originally set up with striped RAID 5, where 2 of the drives were OS. BTW, the two OS drives are on the same controller as the other 10. I know its stupid, but I am did not set it up originally. 

The server was sitting on the floor for a while now with no real use. I tried to boot it up yesterday morning assuming that it would start right up. However, it would not boot, I went into the 3ware bios utility and it just said that the drivers are incomplete. I would rather them be degraded, but it just says incomplete. My fear is that someone put drives into the wrong order at some point, or that the drive('s) may be corrupt. Currently I am running the server off of a live CD. But i cannot get any of the drives to show up in fdisk or mount. I am not sure how to probe for drives yet, I am looking all of that up, but my main concern is rebuilding the raid. 

I am not sure where to go from here. I am trying to figure out if I can probe the drives somehow, and from there maybe use mdadm to then scan and assemble some parts of the array. I don't really know if its possible, and my fear is that I am out of luck. The drives are all identical 250gb WD SATA and are hot swappable. I would appreciate any and all help. Thank you. And if anyone needs any more info please ask. Thank you again.

---

### Post by Odrodzona-Sarmacja on 2008-06-27
Googling with "ubuntu +tutorial +raid" gave me such a nice link:
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)
Does it helps somehow?

---

