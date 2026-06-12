---
title: "software raid , new hdd's ?"
date: 2008-11-13
forum: General Help
---

### Post by rapeid on 2008-11-13
i am trying to setup a software  RAID 0 (raid 1 later ) .. am confused about some basic things since am a noob to RAID systems ..

well if i have an hdd with linux already on it with a single ex3 root file system , can i use it to build a raid 0 with another hdd that am going to add ?

i mean should i change my main hdd to linux raid autodetect (the one with linux installed ) before i attempt to build a raid array ?

or if i start from scratch with 2 new hdd's , how do i do the partitions ... ? partition and format both hdd's with linux raid autodetect file system .. or one with type FD and other hdd with ext3 ?

:confused:

---

### Post by kernelhaxor on 2008-11-13
This should help you: 
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by rapeid on 2008-11-13
thanks , but i have already read that ..

i still cant understand the basic stuffs though .. 


this was my initial setup with which i was trying to setup raid 0

[IMG]http://xs433.xs.to/xs433/08464/untitled753.png[/IMG]

it didnt work , then i read somewhere that > Your original hard drive will not be part of the array .. for whatever reason :confused:

then i added a new hdd , with 3 new hdd's now ... it looked like this

[IMG]http://xs233.xs.to/xs233/08464/untitled2452.png[/IMG]

so i setup my raidtab entry to use hdd1 and hdb1 ..  (am still not sure if the ```
nr-raid-disks 2
``` or 3 ?  since am using 3 hdd's :confused: )

[IMG]http://xs433.xs.to/xs433/08464/untitled3493.png[/IMG]


anyway i was able to intialise the array with ```
mkraid /dev/md0
``` this time 



so few questions still remain ..

1.```
nr-raid-disks 2
``` .. is that correct for my settings or should i change it to 3 ?

2.this was acheived by adding RAID to an existing drive with linux already installed with ext3 file system..

2,a.what should i do to change the ext3 filesystem (linux already installed) hdd to type FD .. is that necessary ?

2,b.if i am using 3 new hdd's . should i partition the all the hdd's to linux raid autodetect before i install the linux OS :confused:






whew .. am sorry if i am confusing you guys .. :(

---

