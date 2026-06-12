---
title: "New Hardware"
date: 2009-12-11
forum: Hardware
---

### Post by ufarmer on 2009-12-11
Hi,

I am in the mood to upgrade all my hardware and I just want to make sure it's all Ubuntu compatible.  Here's what I am thinking of putting together:

Motherboard: ASUS P7P55D Pro
CPU: i7 860
RAM: Corsair XMS3 DDR3 1333 MHz
Hard drives: 4 x 1Tb Seagate Barracuda 7200.12 in a RAID 10
Video Card: ASUS ENGTX275

I am confident that the mobo, cpu and RAM are compatible.  I'm not so sure about the hard drives and the video card.

Any advice is appreciated.

---

### Post by paulisdead on 2009-12-12
It really depends on how you plan on doing that RAID.  If you're dual booting Windows, you'll want to use the motherboard's fake RAID.  Otherwise Linux software RAID would work better.  Either way, you'll need the alternate install CD for those RAID methods.  If you've got a real hardware RAID card, that would be ideal, but expensive.

I can't really say 100% for sure that mobo will work, but it being an Intel chipset, odds are it'll work great.

---

### Post by ufarmer on 2009-12-12
Interesting.  What do you mean by "fake" RAID?  My understanding was that the mother board supported RAID 10 and that a hardware RAID was better than a software one.  I am planning on dual booting with Windoze.

---

### Post by paulisdead on 2009-12-12
What I mean is that the motherboard's onboard RAID is not a real hardware RAID.  It's basically just a driver and a bios that'll let you install windows on it, but is still using the CPU calculate the array, instead of having a dedicated chip to do the job.  A lot of low end "RAID" cards are actually the same thing.  Unless you're dropping a couple hundred dollars on a RAID card, you're probably going to wind up with software RAID of some sort.

Seriously, though, you're going to be running a quad core chip, and will have more than enough spare CPU cycles.

Here's a little guide [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I've not done the fakeraid route, myself, before.  But, I have done Linux software RAID on dozens of systems, and it performs really well.  In fact, it's read performance is better than the real hardware 8 port 3ware 9500s RAID card I have in my server in RAID5.  The newer 4 port 9650 3ware card I got seems to be much better on reads, though.  The 9500s write performance, and system load during huge writes, is still way better than Linux software RAID.  Even with those 2 hardware RAID cards, I still did a software RAID1 just for the OS and email (If you're counting that's 14 hard disks in one box), so software RAID is definitely good and useful.  Since you're doing RAID10, you probably shouldn't see the same huge spikes I had in writing, since RAID5 has to calculate parity data, and that can take up some CPU cycles, whereas RAID 10 is just striping a mirror.

---

### Post by falconindy on 2009-12-12
The issue with fakeraid isn't so much that you're drawing off CPU cycles. As you mention, any modern chip will handle it without flinching. The real issue is how OS's perceive the resultant array. There's plenty of threads (including on this forum) where people have setup fakeraid in the BIOS only to boot off the install disc to find that Ubuntu still sees the 2 drives as separate. It's not a reliable solution. Software based RAID is better given the standardization (inclusion in kernel mainline) of mdadm and lvm.

Hard drives should rarely if ever present an issue with compatibility. They're incredibly simple devices and you should be more concerned with the interface controller (SATA in this case) being able to present the OS with a reference to a valid block device.

---

### Post by paulisdead on 2009-12-12
> **falconindy said:**
> The issue with fakeraid isn't so much that you're drawing off CPU cycles. As you mention, any modern chip will handle it without flinching. The real issue is how OS's perceive the resultant array. There's plenty of threads (including on this forum) where people have setup fakeraid in the BIOS only to boot off the install disc to find that Ubuntu still sees the 2 drives as separate. It's not a reliable solution. Software based RAID is better given the standardization (inclusion in kernel mainline) of mdadm and lvm.

Hard drives should rarely if ever present an issue with compatibility. They're incredibly simple devices and you should be more concerned with the interface controller (SATA in this case) being able to present the OS with a reference to a valid block device.

I'll agree with that.  Linux software RAID is pretty solid, but in order to get the dual boot he wants on it, he might need to go the fakeraid route.

I think it should be worth a shot.  I've removed drives from a system that was setup with fakeraid on an Intel chipset, without deleting the array in the bios first, plugged them into another machine, and the installer still saw them as one volume.  I'm pretty sure that was under debian, though, but it should be a pretty similar situation.

---

