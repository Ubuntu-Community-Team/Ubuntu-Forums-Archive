---
title: "Partion size, Wubi install"
date: 2008-08-14
forum: General Help
---

### Post by nyborjare on 2008-08-14
I have installed Ubuntu 8.04 through Wubi on my D:\ slave HDD 75 GB
C:\ has WinXP

During installation I was asked for size to install to. I took 15 GB

Yesterday I tested to make a backup with "tar". All went just fine but when I looked at the final line when update had finished it mentioned something "No more space on drive". 
Not sure of the wording but I got the impression something had gone wrong and dumped the tar-file in the dust bin :(

If I run gparted and look att my slave HDD the Ubuntu install is done on a 75 GB partition.

If I go to /home/michael and right click there, I find information that I have only 8.2 GB left free space.
Well this would then bee the reminder of the 15 GB used at install.

Being new to all this, can somebody explain.
Give advise how to make sure I can use all the 75 GB for my Ubuntu-play- around-thing.:confused:

Any support in this will be aprec.
Regards

---

### Post by sayakb on 2008-08-14
The / should be atleast 10GB, a swap equiv to your RAM (or 2*RAM for lower RAM sizes) and a /home as per your needs.

---

### Post by Elfy on 2008-08-14
I would imagine that the tar is still in trash unless you've empied it, but you didn't say so.

I'm not sure as I've never used wubi - but it would be logical to me that the remainder of the 75Gb is still there. Does it appear when you run windows that the space is there in your d drive.


Edit - found this in the wubi wiki

> The Windows partition where you installed Wubi is available as /host within Ubuntu All the other partitions will be available under /media/

Wiki is here and worth bookmarking I should think

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by nyborjare on 2008-08-14
My gparted looks like this

Never done this hope iot works

---

### Post by nyborjare on 2008-08-14
Thanks, will read and learn
Regard

---

### Post by ByteJuggler on 2008-08-14
If you just want to be able to access the remainder of the space on  what is "D:\" (75GB drive) in Windows, then you need to simply mount that (if it's not mounted already - one of the other posters explained how.)  If you want to actually enlarge the 15GB of your Windows drive that was allocated to the Linux disk, then that'll require rather more fiddling.  I'd rather not go there unless absolutely required though.

---

### Post by nyborjare on 2008-08-14
Bytejuggler
Thank you for your advice and warning.
I have a tendency to just jump and go.....it hirt's.

---

