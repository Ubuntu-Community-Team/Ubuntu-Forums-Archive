---
title: "ata2.00 exception emask... action 0x2 frozen"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by Terc on 2008-01-14
Please help, I need to have virtualization up and running on this box for my Sr Design project soon, I am able to get through this issue, but I notice multiple pauses during file transfers after mounting my RAID manually once boot is complete.
[[IMG]http://img244.imageshack.us/img244/598/img0096xh5.th.jpg[/IMG]](http://img244.imageshack.us/my.php?image=img0096xh5.jpg)

I found a little help here:[http://ubuntuforums.org/showthread.php?t=651872](http://ubuntuforums.org/showthread.php?t=651872) but it is not possible for me to use this because I am already using all 6 sata slots on my mobo. (4 for raid, 1 for dvd burner, one for OS)

If someone could just clarify what exactly this might mean, it would help quite a bit.  Is my hard drive going bad?  If so, how would I check?

---

### Post by calman on 2008-06-05
Sorry for the super late response, but there could be other people (even if you have solved this) that stumble upon this thread with the same problem.

I once had this problem and when I unplugged my IDE CD drives it went away -- odd.  I've also seen on multiple threads that the problem is often caused by the type of cable that you use.  There might be some difference in SATA2 cords.  I'd just go buy a new one.

You can also try different connectors on the motherboard, but you might have to go into BIOS if you do that and change up the default SATA settings.

---

### Post by calman on 2008-06-21
Actually, I recently had the problem again, turns out one of my CD drives was causing the problem.  I just took it out and the problem disappeared.

---

### Post by argail1980 on 2008-06-21
had the same problem. unfortunately with my system hard disk (IDE). I have found no solution yet and I'm thinking of a possible hardware failure.

---

### Post by calman on 2008-07-06
Like I said, it means your hardware is bad.

---

