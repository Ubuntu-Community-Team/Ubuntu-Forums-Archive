---
title: "Hard Drive Bad Sectors on New Dell Laptop"
date: 2010-10-11
forum: Hardware
---

### Post by jflock on 2010-10-11
I bought a dell studio 1558 laptop about 3 or 4 months ago, and it has 549 bad sectors reported by disk utility on its 500GB disk. The number of bad sectors has increased over time, and seems to be reported by disk utility after a longer bootup time, and a less responsive system after bootup.

I have tried reinstalling and reformatting the entire drive, the bad sectors are still reported. It is currently a dual boot system with windows 7 and ubuntu 10.10. There are also ext4 and fat32 storage partions.

I have run the utilities provided by dell, and they report no problems.

Could anyone provide some advice or help in some way? It would be much appreciated.

I bought the extended laptop warranty, but I am not sure what dell will do if their utilities don't find problems. 

Thanks

---

### Post by efflandt on 2010-10-11
What kind of drive is it?  If it is Western Digital get their DataLifeguard program from [http://www.wdc.com/](http://www.wdc.com/) .  Guess at the drive if you do not know exactly which one it is, the tool should work on any of them.

If it is Seagate or Maxtor get their SeaTools from [http://www.seagate.com/](http://www.seagate.com/) .

They are generally Windows programs, but they may have bootable floppy or bootable CD iso.  They can do a nondestructive test of your drive.

Normally a drive reserves some space to automatically and transparently remap bad sectors to good sectors.  So unless you have some other issue corrupting your drive, if you start seeing bad sectors (especially increasing) that is a bad sign.

---

### Post by jflock on 2010-10-12
I googled the drive model as stated by disk utility, and found the drive to be a seagate one. So I have downloaded seatools for DOS, which runs from a bootable CD to test it.

Thanks - I will post results.

---

### Post by jflock on 2010-10-12
SeaTools reports that my drive has passed both the long and short tests without problems.

So, I am at a loss to explain the bad sectors reported by ubuntu disk utility, and the seemingly related poor performance of my machine. (clean install of 10.10 yesterday, clean install of 10.04 last week)

I am also pretty worried about the drive failing and losing data.

Can anybody help at all? 

Thanks in advance

---

### Post by mikewhatever on 2010-10-12
A number of bad sectors on an hdd is nothing out of the ordinary. I have one with 65000 such sectors. 549 is really negligible, but you should watch the number. If it keeps going up, then there is a problem.

---

### Post by jflock on 2010-10-12
This is the thing - it keeps going up. Or at least, disk utility on ubuntu says that it is. It is now at 594.

I know that this is a relatively small amount compared with the overall size of a hard drive, but I am concerned by the discrepancy between ubuntu's software, namely disk utility, and that of dell and seagate. 

Given that I am also noticing variable bootup times (ranging from 30 seconds to over 5 minutes) and poor performance on initial bootup, I am inclined to think that something is wrong. I also do not have this problem with my other machine at home and work machine, both also running ubuntu.

Is there anything else that anyone can think of that I can try as I have tried reformatting, multiple times infact, but that does nothing. I still have poor performance on initial startup and a long bootup time. I have tried calling dell, and all that they seem to go on is their own utility thing. 

Sorry if these are stupid questions / I am being paranoid, but I am relatively new to all of this.

Thanks

---

