---
title: "Resize partition"
date: 2005-12-01
forum: General Help
---

### Post by ofek on 2005-12-01
I got a normal 30gb hard-drive on my laptop and I want to resize it.
I figured the smartest thing will be trying to do it on a live cd because it wouldn't need to use the hard drive.
Anyways I had breezy's live cd so I poped it into my cdrom and ran gparted through it, picking the size I want it to be and all, but after doing apply it tries to apply for like 5 - 10 min and then stops and get back to the main gparted screen with the old specs of the drive.
Now I realy don't know what to do, I thought that it might be because it uses the swap on that drive but i removed the swap from that drive and got it to another and it didn't help. 
Any ideas?

---

### Post by Iandefor on 2005-12-01
try using the [System Rescue CD]("http://www.sysresccd.org/") to resize; I've had good luck with it. Dunno why Gparted didn't work

---

### Post by Svictor on 2005-12-01
Not an expert myself, but if you try to resize a windows drive, it has to be very neatly defragmented before : from within windows itself, and with some special program ... I forgot the name of the one I used but I can look it up for you if you want. 
Alternatively, you could try qtparted, which is similar to gparted, but included on the knoppix live cd.

---

### Post by ofek on 2005-12-01
Its an ext3 drive not windows.

---

### Post by ofek on 2005-12-01
I tried "System Rescue CD" and it disabels the option to resize on qtparted for some odd reason. 
Any other ideas? I realy dunno what to do. Its not like a regular hard drive that I could get to another computer and resize it there, its on a laptop =/ .

---

### Post by a50sn95 on 2005-12-01
I was unable to get GParted to resize my EXT3 partitions. Said it wasn't supported. Seems that EXT3 partitions made with certain tools can't be done with GParted. I read a post I googled somewhere about converting to EXT2, resizing, and converting back, but it didn't work for me either. This was on a Gentoo drive.
Also, if it makes it easier, or your want to rsync your drive to another, resize, and rsync it back, you can get adapters to put it in a desktop:
[For Instance, here...]("http://www.extremecomputing.com/nothardrivad.html") 
Hope this helps some....

---

### Post by yeahyeahyeah on 2005-12-01
I'm having the same issue (my thread: [http://www.ubuntuforums.org/showthread.php?t=96888&highlight=gparted](http://www.ubuntuforums.org/showthread.php?t=96888&highlight=gparted))

[QUOTE=ofek]I got a normal 30gb hard-drive on my laptop and I want to resize it.
I figured the smartest thing will be trying to do it on a live cd because it wouldn't need to use the hard drive.
Anyways I had breezy's live cd so I poped it into my cdrom and ran gparted through it, picking the size I want it to be and all, but after doing apply it tries to apply for like 5 - 10 min and then stops and get back to the main gparted screen with the old specs of the drive.
Now I realy don't know what to do, I thought that it might be because it uses the swap on that drive but i removed the swap from that drive and got it to another and it didn't help. 
Any ideas?[/QUOTE]

---

