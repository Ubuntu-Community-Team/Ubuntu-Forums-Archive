---
title: "Problems with Plextor PX-712A"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by mark1ewis on 2006-06-21
I've recently converted over to Ubuntu/Dapper after being a long-time RedHat/Fedora user, and it's been a delightful experience.

The only problem I've run into is with my CD/DVD burner, a Plextor PX-712A.  I had it working before I upgraded to Ubuntu, using a vanilla 2.6.15 kernel (first release with full SATA ATAPI support).  I used it to burn my initial Ubuntu CD, but I gave that CD to a friend, and now I'm trying to burn another CD so I can put Ubuntu on my laptop but no love.

Some specifics:

The drive is recognized and assigned /dev/scd0.  I can read discs in the drive.  Syslog messages look just like when I had a working system up until I put a blank disk in the drive.

When a blank disk is in the drive, the drive status lights flash amber and the system experiences long pauses in disk I/O.  When I attempted to burn a disc with cdrecord, the following was printed:

```
Jun 20 22:48:05 merlin kernel: [17179768.672000] sr: Current: sense key: Hardware Error
Jun 20 22:48:05 merlin kernel: [17179768.672000]     Additional sense: Tracking servo failure
Jun 20 22:48:05 merlin kernel: [17179768.688000] sr: Current: sense key: Hardware Error
Jun 20 22:48:05 merlin kernel: [17179768.688000]     Additional sense: Tracking servo failure
Jun 20 22:48:05 merlin kernel: [17179768.752000] sr: Current: sense key: Hardware Error
Jun 20 22:48:05 merlin kernel: [17179768.752000]     Additional sense: Tracking servo failure
Jun 20 22:48:54 merlin kernel: [17179817.016000] ata1 is slow to respond, please be patient
Jun 20 22:49:28 merlin kernel: [17179851.236000] ata1 is slow to respond, please be patient
Jun 20 22:50:02 merlin kernel: [17179885.488000] ata1 is slow to respond, please be patient
```

My SATA controller is an SiS 180.

Anybody have any ideas for how to continue trouble-shooting this one?  I'm kind of at a loss as to how to proceed.

Thanks,
Mark

---

### Post by mark1ewis on 2006-06-21
Oops, scratch that.  Looks like I just pulled a couple of bad blank discs in a row off of the tower.  Tried a couple more discs and everything seems to work.

Still not sure how the drive got into a bad state that apparently hosed my I/O system, but for now everything seems ok.  Ububtu is burning away, soon that crufty old FC3 install on my laptop will be a thing of the past . . .

---

