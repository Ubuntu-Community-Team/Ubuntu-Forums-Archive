---
title: "Can't Format Linux Hard Drive"
date: 2011-01-05
forum: Hardware
---

### Post by Khakilang on 2011-01-05
Recently I was given 2 unit of Dell PowerEdge computer with following spec.

Intel Pentium 4 2.4GHz, 256MB RAM and 40GB hard disk.

It was install with Linux. When loading it hang half way with an error message like Kernel panic. I try to format the hard disk using Ubuntu 9.04 but fail only show blank screen and I also try Window XP but it can't delete the partition as well. So is there a Linux that doesn't allow you to format the hard disk or delete the partition. Is there anyway I can delete the partition and reinstall a Linux Distros or is it just that the hard disk already end of life? ? Appreciate to anyone who help.

---

### Post by cascade9 on 2011-01-06
You could be gettign some hardware issue (could be CPU, motherbaord, RAM, HDD or optical drive). 

If you are confident with hardware, I'd pull the HDD, install a linux distro on a different compter, then reinstall it into the dell.

---

### Post by Khakilang on 2011-01-06
I have try remove the HDD and use another computer to format and re install a Linux Distros but fail. But I did use another HDD and install into Dell and that works. So it is either the HDD fail or somehow the Linux they use got some kind of protection from being formated. What are the odds that the 2 unit of Dell computer had the same problem? Anyone can help? Thanks in advance.

---

### Post by Khakilang on 2011-01-12
Upon booting up I found this error message and it hang.

ide: fail opcode was: unknown 
end_request: I/O error, dev hda, sector 65 
EXT2-fs: unable to read superblock 
Kernel panic - not syncing : VFS: Unable to mount root fs on unknown-block(3,1)

Anyone had any idea what it was? Is the hard disk end of life or is the OS corrupted? Appreciate to anyone who help.

---

### Post by cascade9 on 2011-01-13
That looks like a bad sector to me.

---

### Post by Khakilang on 2011-01-14
I know. Is there any remedy? Like software to reformat the hard drive. I try DBAN but come with an error. I have even use cfdisk but doesn't seem to work. Thank you!

---

### Post by cascade9 on 2011-01-14
There is a basic work around that I know of. 

Figure out where the erorr is, then make sure that you dont try to create a formatted partition there. 

Eg- if you have a 80GB HDD, and the error is at 120MB, you can make a 118MB 1st partition, skip 119-121MB, then the rest of the drive should be fine. (there are more exact ways of describing this, and more exact way to avoid the bad sector, I'm just givign you an overview) 

Warning though, bad sectors like that are normally a sign that the drive isnt very healthy, and it could die at any time.

---

### Post by Khakilang on 2011-01-14
I know but I find it odd that 2 unit of computer, same brand and same hard disk having the same problem at the same time. What are the chance of this happening? Anyway if it die it will die. But I will keep on trying. Thanks for all the help!

---

