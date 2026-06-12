---
title: "sleep on Seagate external hard drive"
date: 2009-11-20
forum: Hardware
---

### Post by potiphera on 2009-11-20
I recently got [this Seagate external drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148406").  It works great (after I formatted it as ext3 and did chmod 777), but occasionally it goes to sleep after being idle for a while.  After that, I can't read or write anything on it, so I have to restart and reconnect the drive.  Is there any way to fix this?  I'm using Karmic.  Thanks!

---

### Post by potiphera on 2009-11-22
(bump)

---

### Post by potiphera on 2009-11-23
(another bump)

---

### Post by potiphera on 2009-11-24
Or does anyone at least know how to turn sleep off on this drive?  I already have "spin down hard disks when possible" unchecked in System>Preferences>Power Management.  This is a total pain; the other day it caused Truecrypt to mess up a volume that had taken several days to create.

---

### Post by growingneeds on 2009-11-25
I'm not too well-versed on the command line. But this web page might help: [http://www.debianhelp.org/node/11551](http://www.debianhelp.org/node/11551)
Please look at the submission by jtones on Mon, 2009-03-30 11:04. I'm fairly certain the answer lies with sdparm command, and it's relevant standby setting.

I have a portable hard drive that I formatted to fat32 because of compatibility issues, I usually avoid the spinning down problem by connecting the hard drive only when it is used.

---

### Post by potiphera on 2009-11-29
OK, I just changed the setting with sdparm, so if I don't post in this thread again, I guess it will have worked! Thanks!

---

### Post by ljonesj on 2009-11-29
I have this exact drive but I dont have that issue as of yet with it. I have the problem of it starting to click with ubuntu and the movies i have on it stop or skip when it clicks if i use my windows machine its fine no clicking and no freexing with it streaming to my mac mini.

---

### Post by potiphera on 2009-11-29
Yeah, I noticed that almost all the reviews on Newegg mentioned clicking.  I haven't gotten any clicking on mine, except one day it started doing it once or twice a second when I plugged it into a laptop, and then it continued after I reconnected it to my desktop computer.  Then after a few hours it stopped, and now it hasn't made any noticeable noises for the past week or two.

---

### Post by potiphera on 2009-11-30
Wait, never mind, I found out that it does still go into standby when idle.

---

### Post by potiphera on 2009-12-05
I would be interested even if anyone knows of an ugly fix involving writing a script to read a file on the drive once every 25 minutes or so.

---

### Post by potiphera on 2009-12-22
This problem only happens with my desktop, and not with a laptop I've used the drive with, and I'm not sure why.  A programmer friend told me I can write a bash script to add a character to a text file on the drive every so often to keep it from sleeping, but he doesn't know of any way to make the script run automatically whenever the drive is mounted.  Is this possible?  I just had a Truecrypt volume which I think got corrupted because of the I/O errors on the drive.  I was able to repair the filesystem, but it was a pain and I'd like to prevent it from happening.

---

### Post by potiphera on 2009-12-26
(bump)

---

### Post by dunskii on 2010-06-29
Ok, I had the same problem with my seagate external drive and found a solution but you need to use windows.  Go to Seagate.com and download their free agent software, you'll find an option to set standby to Never.  Hope this helps.
D

---

### Post by potiphera on 2010-06-30
Thanks! I don't have Windows on any computer around here, but I'll see if I can figure something out.

---

### Post by potiphera on 2010-09-12
Actually I just realized that changing the setting with sdparm does work, except only for however long I keep the drive plugged in.  If I use it on another computer and then on this one again, I need to turn standby off again.

---

