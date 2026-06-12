---
title: "hard disk partition is not recognised!!!"
date: 2009-10-10
forum: Hardware
---

### Post by Anand B.V.K.S on 2009-10-10
I have a two partitioned 120 GB hard disk.
I have vista in one partition(C) and recently installed Ubuntu in the other partition(D)
When I operate on Ubuntu ,I could get access only to the Vista partition.i.e.,(C) :(
Where as when I operate on Vista I could access the entire hard disk.

Please help me out...
I want to access the other partition also from Ubuntu.

Thank you,

---

### Post by shadowlemon on 2009-10-10
How well is your knowledge of Ubuntu?
If you're able to boot in ubuntu you can surely acces it's disc.
Upon install ubuntu will format the disk/partition on which you wish to install.
The root of your ubuntuboot is just your D, even if it's not named D:\ in ubuntu.
in ubuntu it will be named something like /dev/sda[number] /dev/hda[number]

go to console and write "ls /"
this is your D:\ disk.

---

### Post by Anand B.V.K.S on 2009-10-10
Thanks for the reply.

I am a beginner in Ubuntu.

I've installed Ubuntu through windows..

I tried your suggestion but I still cannot access the drive in which Ubuntu exists.:(

I hope you get my question.

When I try to access my root directory by typing "cd /root " it says "Permission denied" ...I wonder why?

Sorry if I disturb you with petty questions.

Thanks again.

---

