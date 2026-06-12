---
title: "Western digital My Book Mirror Edition works in ubuntu"
date: 2009-02-20
forum: Hardware
---

### Post by alasarr on 2009-02-20
I want to buy a western digital hard drive...

[http://www.wdc.com/sp/products/products.asp?driveid=466](http://www.wdc.com/sp/products/products.asp?driveid=466)


it's made up of two hard disk which you can configure in raid 0 or raid 1... it already has a connection usb

Is the raid control in windows software or in the usb box??

If the raid control is in the usb box it dont should have problem but if the raid is in the windows software, it will be a problem because there isn't software for linux

anyone knows if it works fine inubuntu 8.04:p

---

### Post by cmcx_linux on 2009-12-09
To anyone who wonders... I bought one of these and by default they came set up with raid mirror which works great. I use it as / and storage for a sheevaplug wich runs jaunty. The system only saw one hard drive and to make sure that it's not a mistake,I made a partition, copied data to it and after that I swapped hard drives in the case and see if the data exists on both.
From what I could find is that the controller for these, also runs linux on an arm5 with 32mb of ram.

 I know the post is old, but ubuntu forums is a good reference point when googling for stuff, so I think it's worth adding a replay.

---

### Post by diepiapaopolopo on 2009-12-18
That's exactly how I came across this. Thanks for adding your experience.

The documentation seems to indicate that in the case of a failed drive (when in RAID 1 mode) the LED will display a pattern to indicate the problem. Does anyone know if it's possible to detect which drive has the issue without installing the Windows- or Mac-only utility?

---

### Post by sportsdude81 on 2010-01-21
Does anybody know if this HDD will work with Ubuntu karmic 64 bit?  I heard it freezes up on 64 bit vista... but what doesn't :D. No but seriously.

---

### Post by hysterix` on 2010-06-22
> **diepiapaopolopo said:**
> That's exactly how I came across this. Thanks for adding your experience.

The documentation seems to indicate that in the case of a failed drive (when in RAID 1 mode) the LED will display a pattern to indicate the problem. Does anyone know if it's possible to detect which drive has the issue without installing the Windows- or Mac-only utility?

 Hate to bump a 6 month old thread but did you ever figure out the answer to this question?  This is exactly what I've been searching for as I'm paranoid about losing data, but I'm lazy and hate booting my vm to windows to check on the status of the drives.

---

### Post by orangeworx on 2010-09-04
I haven't tried the WD software under WINE but it would be what i would try if i was in ur shoes...
I think i have a bigger problem... when i plug my mirror, OS tries to get access the drive and i get "Unable to mount Not authorized"
any1 have ideas about this ?

---

### Post by cmcx_linux on 2010-10-02
Ok, yesterday I moved some partitions around the hard drive and then, disaster struck, the power flickered and reset my WD. I replugged the drive and for an instant it appeared like 2 units, one with the original MBR and the other with the MBR "after moving" the partition.
The LED started to blink ( as in normal activity) and the hard drive furiously started to work. Then the drive just disappeared  but the activity continued. I concluded that because the power was lost, it started to rebuild the array, and since I modified the MBR, that needed to be corrected as well.
My assumption  was correct, and after 15 minutes it had finished it's work and when I plugged in the unit ( on an ubuntu Lucid amd64 pc) it only saw one disk. It seems that the drive from the first bay is used as a master and the drive from the second bay as a clone of the master. 

Again, old thread but maybe useful for some.

---

