---
title: "Hard drive problems"
date: 2008-11-02
forum: Hardware
---

### Post by Stalker72 on 2008-11-02
I'm trying to set up a RAID 0 configuration. I've used one hard drive for a while, and recently got a new hard drive. The old one didn't work.

When I try to connect the hard drives individually, they both show up, but when I try to connect them both at the same time, only one shows up. I've tried to eliminate problems by switching cables and switching spots, etc.

I have 2 Western Digital SE16 500 GB hard drives. My motherboard is an EVGA nForce 790i Ultra SLI.

Thanks!

Stalker72

---

### Post by cariboo on 2008-11-02
If you are using an onboard raid controller, have a look here:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I used this about a year ago to setup my raid array and have had no problems related to the raid array  since. 

One thing I found it that raid seems to be pretty picky about hard drives, I tried mixing a WD 160Gb with a Seagate 160Gb and it wouldn't work, once I got a matching Seagate 160Gb the raid setup took about 10 to 15 minutes to setup. I have since upgraded to a pair of WD 400Gb drives and again it only took 10-15 minutes to setup.

Jim

---

### Post by Stalker72 on 2008-11-02
> **cariboo907 said:**
> If you are using an onboard raid controller, have a look here:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I used this about a year ago to setup my raid array and have had no problems related to the raid array  since. 

One thing I found it that raid seems to be pretty picky about hard drives, I tried mixing a WD 160Gb with a Seagate 160Gb and it wouldn't work, once I got a matching Seagate 160Gb the raid setup took about 10 to 15 minutes to setup. I have since upgraded to a pair of WD 400Gb drives and again it only took 10-15 minutes to setup.

Jim
I don't have an onboard RAID controller if that is a thing you have to buy seperately.

What I meant was that the **BIOS** wouldn't recognize the two hard drives at the same time, but it recognized both if I connected one at a time.

Stalker72

---

### Post by Stalker72 on 2008-11-03
Bump!

Stalker72

---

### Post by Stalker72 on 2008-11-03
Bump!

Stalker72

---

### Post by psusi on 2008-11-03
Is this IDE or SATA?  If they are IDE and you are connecting them both to the same cable, you need to set the jumpers on one disk to be master, and one to be slave.

---

### Post by Stalker72 on 2008-11-04
> **psusi said:**
> Is this IDE or SATA?  If they are IDE and you are connecting them both to the same cable, you need to set the jumpers on one disk to be master, and one to be slave.
They are SATA.

Stalker72

---

### Post by Stalker72 on 2008-11-04
Bump!

Stalker72

---

### Post by psusi on 2008-11-04
When you connect them both, you say only one shows up?  Which one, and is it still the same one if you swap the connections?

In other words, is the drive that works because of the drive, or because of which port it is connected to?

---

### Post by Stalker72 on 2008-11-09
I managed to solve everything! One of the hard drives' power cable was connected wrong! :)

Stalker72

---

