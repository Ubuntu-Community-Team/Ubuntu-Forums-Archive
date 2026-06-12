---
title: "Help with Deploying a General Purpose Server"
date: 2009-01-13
forum: Installation &amp; Upgrades
---

### Post by solidsnake04 on 2009-01-13
Dear Forumites I hope you are all well and enjoying the new year !
I have an old machine which I would like to set up as a general purpose ubuntu server to practice on, and hopefully learn something about various types of servers.

I have an 80 GB Hard Disk with 1 GB RAM and a fairly decent AMD Athlon 64 Processor.  As the title suggest, I would like to turn this machine into a multi purpose server and have it act as a FTP, Mail, Database, Web, File & Print, Proxy & Reverse Proxy and LDAP server. This setup is strickly for learning purposes just to get some familiarity with the different types of server. 

Moreover, for learning purposes, I also would like to partition this 80 GB HD into:
/
/boot
/swap
/home
/opt
/tmp
/usr
/urs/local
/var 
/srv 
plus whichever other partitions are needed for the services mentioned above. However, I would be pleased if you would suggest appropriate sizes for the partitions and whether I should subpartition  /var. Furthermore, I am not sure about the difference between /var and /srv, so any help would be appreciated. Finally please, advise on wether to have 1 extended partition with all partitions inside it as logical, or 3 primary partitions + 1 extended partition.

PS: The system will have no more than 3 users who shall not use more than 1 GB of data.

I look forward to your help !  ):P

---

### Post by cariboo on 2009-01-13
Seeing as this is an experimental server, and you are probably going to be reinstalling often, I would recommend just one partition plus a swap partition, there is really no need to divide your hard drive into to a bunch of small partitions. I have my server setup like this:

120Gb -- 25Gb /boot 1Gb /swap and the rest for /home
80Gb -- one partition mounted in /home
400Gb Raid1 array one partition mounted in /home

Jim

---

