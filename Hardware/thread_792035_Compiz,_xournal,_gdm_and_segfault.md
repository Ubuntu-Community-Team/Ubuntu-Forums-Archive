---
title: "Compiz, xournal, gdm and segfault"
date: 2008-05-12
forum: Hardware
---

### Post by s1300045 on 2008-05-12
Hi,

I just installed ubuntu on a Gateway m275 tablet pc and had tons of trouble toying with it. First is that, I was only able to shutdown and logout the system successfully periodically. Sometimes the system would go down with the power signal still on, and more often the hard drive would, too. I had to press the power button for four seconds to shut the system cold. I tried adding apm to both /etc/modules and boot but that seemed not helping at all. I looked up in the log and found out gdm was having segfault before I restarting the system, would that be the problem? How do I fix it?

Another thing was that, when I used xournal for note keeping, the system would froze up randomly and forced me to reboot. The cursor was still moving, but I am not able to write/draw/click/type anything, and ctrl+alt+backscpase/del was unresponsive. I ried to reopen the journal automatically saved by xournal and the system hanged up, too.

Last but not least, I was not able to rotate the screen with compiz turned on. I did some research and found out it's an intel graphic card driver problem. This made me become suspicious that maybe that's all that's causing the trouble. Had anyone experienced these same issues? I was going to try increasing the graphic card memory in bios but I was at work when I typed this, and I wasn't sure if the bios had such an option for that.

Sorry for the long rant and bad English!:)

---

### Post by s1300045 on 2008-05-12
There is something I just found out. My video card only got 8 mb of shared ram, was that the problem?

bump

---

