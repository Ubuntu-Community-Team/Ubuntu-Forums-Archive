---
title: "Minimise hard disk activity (oh the noise!)"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by chochem on 2008-02-28
I'm getting annoyed at those constant (every five seconds) ticks the hard disk is making when there are no discernible causes for it. So my questions are 
a) are there any usual suspects? some universal continually runnning process that does this kind of thing?
 b) is there a simple way to tell what services/programs are accessing the hd at any given time and 
c) is there a way to just generally reduce harddisk activity? free reports about 500 Mb of free memory plus another 250 MB cached (out of a total of 1Gb). I don't suppose there would be a way to put this to use in the service of quiet, would there?

---

### Post by Average Joe on 2008-02-29
a) Usual suspect: [Hard Disk Load Cycle Count issue]("http://ubuntuforums.org/showthread.php?p=4376943")
b) I wouldn't know.
c) If the problem is the usual suspect mentioned under a) you could try:
```
sudo hdparm -B 254 /dev/sda
```
assuming that your drive is sda. That will almost disable completely the Advanced Power Management feature of your drive and might stop the clicking.

I have had a similar issue with my hard disk. I solved mine like [this]("http://ubuntuforums.org/showthread.php?p=1728044#post1728044").

---

