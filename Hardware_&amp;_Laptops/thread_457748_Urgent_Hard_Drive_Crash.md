---
title: "Urgent Hard Drive Crash"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by joshlfisher on 2007-05-29
I ran fsck on my system, answered y to all, and boom, my home partition is gone!
I tried installing linux again, and not format my home partition, to see if that would help, but NO, it appears that all my data is gone. the wierd thing is that the partition still shows the same used and free space. If there is any way to get the data off the partition, I REALLY need to know how.
CAN ANYONE HELP ME PLEASE!

---

### Post by drosenbauer on 2007-05-29
I've dealt with a lot of drive issues. Step one is to unmount that partition NOW and do not use it until you recover the data. If you've already created new data on the drive, your data may be beyond recovery.

Next, search Google for free programs that will allow you to recover damaged filesystems. I found a program that did this several years ago when I accidentally reformatted a partition. (It didn't work for me because it found the newly formatted partition that was already on there.)

Finally, wait for somebody else to come on here and tell you something about superblocks, because I don't know enough about them.

---

### Post by joshlfisher on 2007-05-29
Thank you. I am looking for programs and have found a couple that I think will work. I AM interested in Superblocks, and would love to have an explanation.

---

### Post by Bigdog60 on 2007-05-29
Dude if you created a new partion you arent going to be able to recover it.

---

### Post by joshlfisher on 2007-05-29
I haven't messed with the partition that is in question. I don't have anything worth keeping on hda1 (root),
it's just hda2 (/home) that is giving me fits.

I found a program called Stellar Phoenix Linux that can recover files on EXT3 partitions. So far it appears to have found all my data, but it is still looking and taking an EXTREMELY long time. I really don't mind the time If I get my data back. Once I have everything in a safe place, I'm gonna wipe the drive and start form scratch, then restore my data.  I keep my progress posted here, so anyone else can benefit.

Thanks for the help folks!

---

### Post by regomodo on 2007-05-31
how's it gone. I'm in a major pickle right now too

---

### Post by Tilo on 2007-05-31
when you get fsck errors, it is a VERY VERY BAD IDEA to try to re-install LINUX (or write ANYTHING to the harddrive at all for that matter) and assume this would make things better... 

If you get a fsck error, take your time to fix the problem, get a second drive to re-install LINUX, and don't touch the corrupted drive with your valuable data.. 


I wrote up a page on forensic LINUX tools.. maybe this might help:

    [http://www.unixgods.org/~tilo/disk_rescue.html](http://www.unixgods.org/~tilo/disk_rescue.html)

I would suggest to use dd_rescue - to create an image of the broken harddrive, and then to 
try to do any repairs to the image -- not to the actual broken harddrive...

    [http://www.garloff.de/kurt/linux/ddrescue/](http://www.garloff.de/kurt/linux/ddrescue/)

You will need a separate (bigger) harddrive to put the image on - and perhaps you will want to 
make more than one image, to try several tools.. 

Good Luck!

---

### Post by Tilo on 2007-05-31
how much critical, non-reproducable data do you have on that drive? 

If you can reproduce most of the data, it may not be worth trying to rescue the data.
So if you have a backup that would save you a lot of time.

You could also try to run fsck with a different superblock, e.g. 

   fsck.ext3 -b 8193 -f -n -p -v 

please use this command with -'n' enabled first!! to see if you find the correct secondary super block.  the above command will not alter your filesystem - it will just let you know what it would
do if you would run it without '-n'

Please check "man fsck.ext3" for the location of the super blocks.. 

Good Luck!

   T.

---

### Post by regomodo on 2007-06-01
> **Tilo said:**
> how much critical, non-reproducable data do you have on that drive? 

If you can reproduce most of the data, it may not be worth trying to rescue the data.
So if you have a backup that would save you a lot of time.

You could also try to run fsck with a different superblock, e.g. 

   fsck.ext3 -b 8193 -f -n -p -v 

please use this command with -'n' enabled first!! to see if you find the correct secondary super block.  the above command will not alter your filesystem - it will just let you know what it would
do if you would run it without '-n'

Please check "man fsck.ext3" for the location of the super blocks.. 

Good Luck!

   T.

Yeah, i had tried to find the backup superblocks. It had none. God knows what i did to ess up that drive so badly.

I've conceded defeat with my drive and reformatted it. It had a lot of work on it but i've been through this before. ****

---

### Post by Tilo on 2007-06-04
to find where the superblocks should be, you can do this:  mkfs.ext3 -n -S /dev/your-device
BE VERY CAREFUL WITH THIS!

I stuck a '-n' in the above command, so you will run it without changing anything. 
If you remove the '-n' , it will create new superblocks for your partition - don't do this on 
a healthy partition - this is a last ditch attempt only!


Sorry to hear that you already re-formated your drive - i'm posting this, so it gets archived in the thread - perhaps it will help somebody else..

---

