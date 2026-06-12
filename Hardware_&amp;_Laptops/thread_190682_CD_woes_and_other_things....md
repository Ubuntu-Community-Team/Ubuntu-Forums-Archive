---
title: "CD woes and other things..."
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by pzipfel on 2006-06-06
Hello all,

I almost hopped on the ubuntu bandwagon a year or so ago, but now I have finally gotten around to installing Xubuntu on an older laptop:

Dell CPx
PIII 600mhz
128mb memory
20gb harddrive

everything outside of the cdrom drive and wireless card worked find from install.  I figured the wireless card would be a problem, but that was something I thought I could handle.  When installing Xubuntu (using the alternate CD and text install) I got a mouting cd-rom error.  I attempted to remount the CD drive again and got no errors so I continued on as normal.  Everything looks fine on the desktop.  After playing around a bit, trying to figure out the internet settings, I realized that I had to get ndis-something off the install cd with synaptic.  However, synaptic doesn't recognize my cd is there and I can't for the life of me figure out how to check to see if Xubuntu sees my hardware (ie. cd-rom, wireless card, mouse, nothing).

So I'm kind of stuck here.  I'll admit this is my first Linux install.  Most of my questions were answered on the wiki or forums that I've been browsing, but I haven't found anything on this yet.  Any help would be very appreciated.  I just want to know what to do about the CD-ROM so that I can try to figure out the wireless stuff on my own.

Thanks,

Paul

---

### Post by pzipfel on 2006-06-09
OK, after playing around for just another 5 minutes I've realized alot more about this system and the cd thing was just a mis-understanding.  The cd error I got while installing was a missing release file?  or something along those lines that hasn't caused me any other problems since I re-installed.

However, I've just about exhausted what I can find on my wireless card, so naturally I'm coming here to see if anyone can help.  I have a Belkin F5D7010, which I was thrilled to find out works right out of the box.  That was until I found that it was rev2 ver4000.  the chipset is broadcom bcm4318, but I haven't been able to get ndiswrapper to work with the original windows driver.  I also have checked the wiki for the bcm43xx page and it didn't work either apparently.  I am using the bcmwl5.inf driver.

If anyone has any suggestions, I would be grateful, or if you need more info about the system to answer my questions, let me know.

Paul

---

