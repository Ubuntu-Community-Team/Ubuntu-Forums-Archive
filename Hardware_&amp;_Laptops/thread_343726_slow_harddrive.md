---
title: "slow harddrive ?"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by cytg on 2007-01-21
relative to this 

[http://www.ubuntuforums.org/showthread.php?p=2042685#post2042685](http://www.ubuntuforums.org/showthread.php?p=2042685#post2042685)

im investegating another 'issue' .. i think i might be looking at some poor harddrive performance here

brandnew ata133 500G hitachi drive, popped in old kta133a/700mhz K7 system(ata100 pata controller)

to test the readspeed of said disc i did this

cp 350M_FILE /dev/null

and took the time, just over 20 seconds. Thats about 17megs /second. Not quite what i expected

hdparm to the drive reveals what's in hdparm.conf wich is

hdparm -d1 -m16 -c1 -Xudma6 -A1 /dev/hda

..... comments please ? :)

---

### Post by cytg on 2007-01-22
hilfe ?

---

