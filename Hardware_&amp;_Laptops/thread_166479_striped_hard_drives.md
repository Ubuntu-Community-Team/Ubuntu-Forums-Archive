---
title: "striped hard drives"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by Tortanick on 2006-04-26
I would like to stripe everything across 3 hard drives, so if one fails I can just replace it and carry on like there wasn't a problem. How do i do this?

---

### Post by savas on 2006-04-26
Hi. I don't know a software solution for doing this. But there is a famous hardware solution called raid 1. If your main board supports raid level 1(nowadays most mainboards supports raid 0 and 1) you can do this easly. You plug two harddisk that have same properties(especially same sized). But i don't thing there is a main board that supports raid 0 on tree disk. If you have four harddisk you may use raid 0 and raid 1 at the same time. Thus you can gain speed in addition to the information safety. Good luck.

---

### Post by savas on 2006-04-26
A final note you may find below links usefull.

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)
[http://www.linuxjournal.com/article/5653](http://www.linuxjournal.com/article/5653)

---

### Post by Nequeo on 2006-04-26
[QUOTE=savas]A final note you may find below links usefull.

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)
[http://www.linuxjournal.com/article/5653](http://www.linuxjournal.com/article/5653)[/QUOTE]

These are very good links. But in case it is not made clear by these articles, for data redundancy you want mirroring, not striping. I would suggest a RAID-1 set-up with one spare drive. That way if one of the two drives in use fails, your data will be mirrored onto the spare HDD. 

[EDIT] You could always just use RAID-1 or RAID-5 across all three drives... But my gut feeling is that having one not constantly being written to will prolong it's life, and still leave it there in case it is needed in the event of a disc failure. Go with RAID-5 if write speed is important. RAID-1 if your primary concern is the safety of your data.[/EDIT]

Otherwise, if you can get a fourth HDD, go for RAID-5, like Savas said.

The other thing I would mention is that I had no luck with my KV8 motherboard using hardware RAID. But when I disabled the Hardware RAID ROM in my bios my SATA drives were detected and I had my software RAID-1 set-up working in about five minutes. 

I used to have a 80gb drive with Windows, Ubuntu 5.10 and my data, and a 40GB drive with Ubuntu 6.06 and more data. Now I've booting Ubuntu 6.06 off the 40GB drive, running my home partition off a 200GB RAID-1 array, and gave the 80GB drive to my girlfriend. 

One other, other thing. Don't buy Maxtor drives if you can help it. I've seen 500 of those things die in the space of five months at my current company. I use Seagate's, and I've had a very good run with them. I've accidentally hosed my MBR once or twice, but I've never had one die on me before I replaced it.

---

### Post by Tortanick on 2006-04-27
Thanks for the help, 

I'm not sure about the 3 live drives or one sleeper 2 live drives option. 

On the one hand drives can sleep forever safely but on the other hand taking an old, and only, drive and copying the entire thing to a new one after a failure sounds a bit risky. 

Still with those articles and knowing what to google for It'll be smooth sailing from here on :)

[Edit] I found mention of a software RAID in those articles 
[http://freshmeat.net/projects/mdadm/](http://freshmeat.net/projects/mdadm/)

Whats the advantage and disadvantage to useing software rather than hardware?

---

### Post by savas on 2006-04-27
I think main difference is performance. Software version must be run slower than hardware version.

---

### Post by Mavric25 on 2006-04-27
Tortanik,
   If your MOBO RAID supports RAID5 you can build it with 3 drives, that's all the drives that required for it (3+).  You will effectively lose the storage space of one entire drive by using RAID5, howerver if one drive fails your computer will not crash.  You then shutdown your computer and swap the failed drive with a new one.  Oh, and be sure to note which drives are which if this is IDE or SATA as there isn't IDs like SCSI and if you replace the wrong drive your likely to mess up your RAID config.  RAID0 is a true strip and has no fault talerance...so if you lose one of the 3 drives you are in deep.:)  But the point is that you can strip or configure a RAID0 with 2+ hard drives.  With RAID0 though, the more drives you have the more dangerous it is, because you are increasing the likely hood of a faulure, of which it only takes one to lose all the data. :)  I'm not sure how to setup Ubuntu on my system as I've already got 2 OSs running fine on the 3 drive SATAII RAID5 set I configured and I want to add Ubuntu for a tri-boot on a 3rd partition.:)  If you have any thoughts let me know...thanks.:)

---

