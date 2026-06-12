---
title: "Laptop harddrive load cycle count under Wubi"
date: 2008-11-08
forum: General Help
---

### Post by futuroimperfetto on 2008-11-08
Hello,

 I've installed Ubuntu 8.10 through Wubi on a friend's laptop (a Sharp PC-MR80j from 2005). 

I've known for a while that Ubuntu suffers from issues of power-management because the disk parks or spins down too often. I am referring to the issue described in this post:

[http://ubuntuforums.org/showpost.php?p=5031047&postcount=3]("http://ubuntuforums.org/showpost.php?p=5031047&postcount=3")
[B]
QUESTION:[/B] Do I need this fix for Ubuntu running on Wubi?

I have decided to use the fix mentioned in the previous link which points to the following solution:

[http://en.opensuse.org/Disk_Power_Management]("http://en.opensuse.org/Disk_Power_Management")

We create two files and them activates them through this command:
```

pm-powersave true
hdparm -I /dev/sda | grep 'Advanced Power'

```
However, unlike what happens with the other laptop I tried this on, I don't get the confirmation asterisk.

**QUESTION:** How can I check if what I've done is working? Otherwise, how can I make sure that it works?

Thanks for reading this

---

### Post by Vadi on 2008-11-08
Unless you actually know of this issue, you don't need to fix it. You'll know about if you hear the harddrive clicking often.

For me personally, this hasn't been an issue anymore lately. I think they fixed it

---

### Post by futuroimperfetto on 2008-11-09
Hi Vadi,

 Thanks for your reply! You are right: I just noticed they fixed it on Intrepit Ibex:

[http://brainstorm.ubuntu.com/idea/288/]("http://brainstorm.ubuntu.com/idea/288/")

I list one hard drive due to this issue before and apparently another one is at risk (as my new laptop's heads park 144 times per hour. My new laptop has Hardy on it). I should probably switch to Intrepid as well.

Cheers!

---

