---
title: "Slow USB HDD"
date: 2009-07-26
forum: Hardware
---

### Post by graphicsxp on 2009-07-26
Hi,

I've got an external hdd 500 Gb USB 2.0, but often the transfer rate is 1Mb/sec. However it's not always like that.
I've run hdparm while my hdd was having this issue and the output shows it should work as USB 2.0 :

sudo hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:   742 MB in  2.00 seconds = 370.46 MB/sec
 Timing buffered disk reads:   92 MB in  3.02 seconds =  30.51 MB/sec

Yet, if I transfer a file (700 Mb), it is painfully slow.... 

What can I do ?

---

### Post by dark.shades on 2010-09-27
well i have the same problem with my transfer it started when i move lots of Gb to my internal drive
i didn't find a solution yet but if you copy them folder by folder you will finish faster than copying them in one bunch 
i know its not a solution but that how i can transfer files 

i wonder if i can use Tera copy from windows with wine does it work ?
i will see if it works

---

