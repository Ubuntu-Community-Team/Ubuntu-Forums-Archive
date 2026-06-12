---
title: "Partition table of hard drive is messed up..."
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by eatmycow on 2007-03-03
I have previously had a few problems with dapper drake and also suse 9.3 and usb hard drives causing partition tables to be deleted, because of this i have noted down what the partition table of my usb hard drive is. When it has happend before I just boot from a partition magic 8 disk and edit the partition table and all works well after that.

Today however I was trying to make a file server (using dapper drake server) and all was  going fine until i connected the hard drive and it didnt mount it. I checked what was mount and found that it didnt like the partition table. I reconnected the usb drive to another computer (its easier as the other server is under the stairs) and loaded up partition magic. This is where i found something was more wrong than usual. The size of the hard drive was incorrect (is 300gb so should register at about 280) and also more alarmingly it came up as 2 separate drives (the values of these didn nt add up to the correct amount). The information in the partition tables themselves didnt make any sense at all (the partition type was set top 6A which i cant find any information about). Also when I tried to edit any of the information the changes were not saved.


Note partition Magic shows correct data for my other 2 hard drives.
The drive that is broken is a maxtor Diamond Max 10 300gb
And the other two drives are western digitals  

I am currently uploading a video to you tube to show what happens when i edit the partition table, I will post a link when it finishes


Edit: Here is the link for the video [http://www.youtube.com/watch?v=gW8F5-F5iHM](http://www.youtube.com/watch?v=gW8F5-F5iHM)

---

