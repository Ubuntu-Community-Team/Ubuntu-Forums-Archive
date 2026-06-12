---
title: "&quot;Recovering&quot; a RAID 0 set up (2 disk)"
date: 2013-09-30
forum: Hardware
---

### Post by NickJohn on 2013-09-30
Ok so I have been round the threads already and it seams like most people get to fed up with this before they get round to solving it and take the easy route out.
I cant take said easy route out.
So the issue, friends pc's motherboard failed. they had a RAID 0 array made up from 2 disks each 160GB.
I have looked at setting up the disks under windows but this is a going to cost you a lot for the software thing. So after hours of searching I am starting to get the picture this is a comon issue but people have tried and succeeded in getting the raid array to fire back up again. 
I am using sudo /sbin/dmrraid -r But all I get back is a list of the two drives that were in the RAID array but -- ERROR: isw: could not find disk {disk address /dev/.....] in the metadata.
How can i edit this metadata so they are in it WITHOUT reformatting the disks?
They are currently in a diffrent PC in a HDD dock. I am sure I know which disk was disk 1 and which was disk 2.
Any help asap would be great, after this I am going to wright a thread / how to for others.

---

### Post by NickJohn on 2013-09-30
I have made some head way using [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)
but i am havving truble understanding what the outputfile.txt should like like when i hit it on the head

---

