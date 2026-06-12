---
title: "Hard drive problem"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by medeshago on 2006-09-18
I was trying to install ubuntu 6.06 in my girlfriend's computer but i couldn't because it said that there was no hard drive available. Then i wanted to format so i tried with qtparted (using SystemRescueCD), but it also didn't find a hard drive... I can't install or format and i really need help.

---

### Post by jimbren on 2006-09-18
Is is saying there is no hard drive, or no space available?
I'm guessing that you're wanting to do a dual boot with Windows, and it is telling you that there is no space available.  

If that's the case, itis most likely because the hard drive is heavily fragmented with data, and the partitioner can't find enough available space to install.  To fix this, you need to defragment the drive from within Windows.  Start\Programs\Accessories\System Tools.

Once this is done, you should be good to go.

If you're not doing a dual-boot and still having problems, try to post exact error messages, along with whatever stats on your hard drive that you can dig up.

Hope this helps, 

jimbo.

---

### Post by medeshago on 2006-09-18
It says that there is no hard drive at all. I don't want to do a dual boot, i just want to format and i can't. The installation wizard and qtparted (running System rescue cd) say that there is no hard drive in the computer.

---

### Post by jimbren on 2006-09-20
Okay, this might seem stupid, but do you currently have an OS installed on the machine?  If not, does the BIOS see the hard drive accurately?

---

### Post by SoloSalsa on 2006-09-20
Hey!  I know what you are talking about!
   So, once I tried Gentoo.  I did **nothing** to the drive.  I just booted from the disc, it said like loading or something, then I saw the top-left quadrant of the Gentoo logo.  Apparently, it thought the 800 * 600 screen was 1600 * 1200  (like the highest resolution screen there is, and exactly four times mine).  Well, I couldn't see anything like that, so I forced off and forgot about it.
   Next time I turned on the computer, Ubuntu loaded, but I could not do anything with my second partition! As if it hadn't existed!  So I booted to gparted, and it NEVER found the disk...  Just finding devices, or whatever the caption was on the bottom.  My master boot record must have been screwed up; in a Linux-UNFRIENDLY way.  I couldn't change it at all! No repartitioning, even. *Gasp*
   Anyway, I reinstalled WIN98 from the system recovery disc (OEM).  I had no way to keep stuff from that partition.  *Sigh*  But it's just proof, that gParted AND Ubuntu truely could NOT find the drive.

---

### Post by medeshago on 2006-09-22
now it's running windows xp (it's my girlfriend's computer), and no, the problem it's not only on linux, I can't reinstall windows xp.

---

