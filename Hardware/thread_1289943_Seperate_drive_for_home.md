---
title: "Seperate drive for /home"
date: 2009-10-12
forum: Hardware
---

### Post by redsoxreed on 2009-10-12
Hi there, 
If I had a small solid state drive (32 gigs or so) along with a much larger SATA drive, with Ubuntu installed on th SSD and /home on the SATA drive, would there be a significant speed increase?  Will the time it takes to move data between the two hard drives cancel out any speed increase from the SSD?  Thanks.

---

### Post by sgosnell on 2009-10-13
Probably not.  The access time isn't going to be that much different, and even if one takes twice the access time, you won't even see it.  Transfer speeds are comparable, so I don't think you will really notice the difference, unless the HDD is a very old and slow one.  Speed isn't really the reason for using SSD.  Reliability in a rough environment and lower energy use are the real reasons.

---

### Post by redsoxreed on 2009-10-13
Ok, thanks for the insight.  :)

---

### Post by cascade9 on 2009-10-13
Umm..SSDs have virtually no access time. 0.1 MS is typical for SSDs, 10+ MS is typical for HDDs. Transfer speeds can be over 2 x HDD speeds. 

You should notice a difference if your use a SSD, and boot times in particular should be lower....provided you get a good one. Some of the SSDs are awful. 

You might 'lose' some of that speed if you have to copy data from the SSD to the HDD, but wouldnt you setup your system so that everything you d/l (or play with in other ways) go to /home?

---

### Post by redsoxreed on 2009-10-13
Ok, so if I install an application in a folder on the 32 gig SSD (in /bin or something) but I have it work with files saved in my /home drive, there should be a speed increase?

---

### Post by nzadLithium on 2009-10-14
The only thing that will speed up is the time required to load the files into ram. If you run a program it is loaded into ram so if the program is on a solid state drive it will load faster (you really wouldn't notice the difference though). If you then used that program to open files on a standard hard disk it would take the same amount of time to load those files as it would before, as they are not on the faster drive.

---

