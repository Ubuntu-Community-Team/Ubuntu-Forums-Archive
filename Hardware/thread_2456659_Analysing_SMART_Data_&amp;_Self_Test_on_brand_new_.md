---
title: "Analysing SMART Data &amp; Self Test on brand new HDD (Lenovo M75q-1)"
date: 2021-01-16
forum: Hardware
---

### Post by username2758 on 2021-01-16
Hi,

I have just purchased a new mini-PC from Lenovo, the M75-q1 and it features the following hard disk drive: ST1000LM049-2GH172 (LXM4).

As you can see from the screenshots taken from the 'Disks' utility, the number of read error rate and seek error rate is significant (short SELF test). Does that mean it's almost failing?

Also, the temperature of the hard drive disk is constantly reaching 50 degrees. Is that okay too?

What else can you say about the overall health of this hard drive?

PS: the M75q-1 is currently running in single-channel memory mode which I'm not sure has any impact on memory-related issues including the HDD.

---

### Post by TheFu on 2021-01-20
Can't read the images. Sorry.  Best to use CLI tools and post text [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) wrapped in code tags, please. 


I always use **smartctl** to capture SMART results after doing tests.
Weekly short.
Monthly long.
Comparing how the data changes over time is the best way.
 
Every HDD has different operating conditions.  Read the specs for that exact model to determine whether external cooling is needed.

---

### Post by deadflowr on 2021-01-20
The read error rate is a particular issue with Seagate drives.
Not a problem.
See: [http://www.users.on.net/~fzabkar/HDD/Seagate_SER_RRER_HEC.html]("http://www.users.on.net/~fzabkar/HDD/Seagate_SER_RRER_HEC.html")

---

