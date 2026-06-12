---
title: "NOOOO!! Thinkpad horror!"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by ushaba on 2007-09-16
Earlier today, while sitting on my couch using my thinkpad, I got up quickly to get the phone and accidentally tripped over the ethernet cable for my thinkpad. This is a new apartment, so this general act of stupidity is in part due to the new cable layout, but still, what follows is obvious. The thinkpad was pulled down from the couch onto its' side, resting on the side with the cd drive and hard drive, and the side of the monitor. The screen was not injured, and even displayed my Kubuntu desktop until I turned it off. I turned it back on to discover that I can boot to grub, but am unable to get into any kernel setting for kubuntu, or windows xp. if i try to boot into windows, it tells me a file is missing. if i try to boot into kubuntu, i get "out of memory" or when i try to boot into a live cd with the hard drive turned off in bios "crc error...out of memory." as this is a thinkpad, this worries me to no end, and the thinkpad has performed like a trooper just until its warranty ran out a couple of months ago. from reading online, it looks like the problem is most likely a bad board, whcih is of course the worst possibility, but i guess some people suggest the possibility of a bad hard drive, a loose ide cable (i tried opening the case, but it's almost impossible to get in the hard drive area),  etc. I can get to the main menu of the Kubuntu, but not much beyond it. when it's loading initrz.gd i get the crash with crc error - out of memory. otherwise i just get "system halted - out of memory" could this be a bad stick of ram? any help for my ailing thinkpad t40 (which is like a child to me) would be welcome.

---

### Post by poe503 on 2007-09-16
The first thing I would do is check that the memory module wasn't jarred loose.  As you have suggested, the hard drive connection may also have come loose.  Good luck.

---

### Post by ushaba on 2007-09-16
when you say the memory module, i assume you are referring to the sticks of ram? i reinserted both of them, which hasn't had much effect...

---

### Post by poe503 on 2007-09-16
Yup, sorry to say I can't think of any other EZ fixes at this time. :(

---

### Post by trippinnik on 2007-09-16
It sounds like it could be the hard disk.  My thinkpad has a bay that opens up to the hard disk.  you could check it's not loose.  Also you could try booting up with the live disk, if everything works you can eliminate the ram, board, etc as the problem.  There's also a choice for Memtest. If you have an external drive you can try backing up the data if you can retrieve any of it and then try formatting again, it may just be corruption and not totally destroyed disk.

---

### Post by Z_Cee on 2007-09-16
I'm not that familiar with Thinkpad's, but you commented that you reseated "both" sticks of RAM. Try swapping out each stick of RAM with the other and boot using only one stick at a time. It's worth a try? 

Completely remove and reinstall the hard drive as another choice.

---

### Post by ushaba on 2007-10-13
My thinkpad is back in action! In the event that someone else has a similar problem, it turned out there was a problem with the CPU, as well as a need for some minor resoldering on the board. this whole transaction was conducted l in Cantonese, so a detail or two might have been lost. I just wanted to thank everyone for their suggestions and let someone facing a similar problem in the future know what was the issue!

---

