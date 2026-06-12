---
title: "suggestions for disk setups for install?"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by ljwobker on 2009-01-01
I'm building a new install for a box that will primarily be a fileserver, but also other random things along the way.

I'm considering setting up my disks in the following format, but wanted to ask the collective group for any suggestions or improvements over what I have here.

Physical disks:
1x old 36GB raptor (this will be root, boot, swap, etc) -- eventually I'll probably replace this with a basic solid state drive for added reliability and since I don't need very much space anyway, but I have the old raptor lying around.  Logic here is that I don't want to mess with running the system on RAID (no performance concerns) and it seems like having the OS on a small, separate drive makes sense when I have the space in the case anyway.  

2x 1TB seagate SATAs -- I'm planning on INITIALLY setting up a two-drive RAID 5 array, the logic being that when I add a third drive I can just grow the array.  This is opposed to initially setting up a RAID 1 array and then converting it to RAID 5.  Anyone see any problems here?

right now I'm planning on running LVM, but I'm not 100% clear on how the LVM <--> mdadm interaction works, any thoughts here would be greatly appreciated.  

I plan on basically creating one very large /home mount in the LVM that runs on top of the RAID -- is this the right way to have expandability in the future?  I *think* I can just add another drive, grow the RAID 5 array, and then extend the LVM volume and /home magically gets bigger... yes?

So... what have I not considered?  ;-)      thanks!

---

### Post by doglover56 on 2009-01-01
Doesn't a RAID 5 require at least three drives? Didn't think it was even an option with two.

IMF

---

### Post by ljwobker on 2009-01-04
I've found examples where you can give mdadm raid-5 and two-drives options -- but my gear hasn't arrived yet so I'm not 100% sure.

---

### Post by ljwobker on 2009-01-09
For googlers who find this:  2-drive RAID5 arrays are definitely possible and work as you'd expect.  See:  [http://ubuntuforums.org/showthread.php?t=1034722](http://ubuntuforums.org/showthread.php?t=1034722)

---

