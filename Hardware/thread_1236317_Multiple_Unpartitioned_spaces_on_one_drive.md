---
title: "Multiple Unpartitioned spaces on one drive?"
date: 2009-08-10
forum: Hardware
---

### Post by Fateful Ikkou on 2009-08-10
Listen i "really" need help i am using Ubuntu linux ver. 9.04 due to viral infection of 
Win XP, I tried to install Ubuntu so many times (equal to 8-9 hours of work) and couldn't get anything to work.

Finnaly after 7 hours of work i got it to actually begin installing on an 8GB                SONY Flash Drive i "Borrowed" from my older brother (He knew this of course) and about 73% into the installation i got an install error than BAM! I could no longer Mount the drive and when i reformatted it using my older bro's laptop i popped it back in, wouldn't work

So i then loaded up a win xp install Disc on my laptop to access the partition Manager and got this strange Setup on that disk:

Unpartitioned Space                  212 MB
Unpartitioned Space                 4087 MB
D:/ Partitioned Space               3342 MB

I then preceded to Erase the Active Partition and recieved the Following

UnPartitioned Space               3342 MB
Unpartitioned Space                  212 MB
Unpartitioned Space                 4087 MB

I the asked myself the question, Why and How? then preceded to try and create a partition in one of the Unpartitioned Spaces and recieved the Following:

"The disk you selected is a removable drive that is already partitioned. Win XP does not support the Creation of Multiple Partitions on a removable drive."

"You can select another disk or delete the partitions that already exist and then create a new partition."

I would do what it said, but i can't delete an Unpartitioned space...Right?

I would Really appreciate anyones help on the matter because i really don't want to buy another drive to replace the one i ruined.

           Thank You

---

### Post by Cheesemill on 2009-08-10
For some reason Microsoft has decided to not support multiple partitions on removable drives.
 
You can use gparted running from a Ubuntu Live CD to repartition your drive.

---

### Post by Fateful Ikkou on 2009-08-10
that wont work because of the following reasons:

1 - I need to restore the entire allocated space to 8GB instead 3 Unpartitioned Spaces

2 - As i said before i can "not" access the Drive in _**Ubuntu**_ It wont even show up.

3 - I cannot partition all 3 spaces to a total of 8GB it is impossible....

4 - In windows when i popped in the drive after all this it still showed up that one partition was available, also in Ubuntu when it did recognize for awhile it said there were 2 partitions when actuality there was only 1 partioned/usable drive and even that wouldn't mount in Ubuntu

5 - This really sucks

Also im sorry if i come off as a little huffy but it is only because i am "REALLY" tired sorry in advance...

---

