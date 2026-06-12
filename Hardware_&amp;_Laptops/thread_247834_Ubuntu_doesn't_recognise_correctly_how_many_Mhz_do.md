---
title: "Ubuntu doesn't recognise correctly how many Mhz do I have."
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by zzzname on 2006-08-31
I have recently installed a Ubuntu Dapper on my Thinkpad X30 and everything is working fine except that when I check /proc/cpuinfo it shows:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 11
model name      : Mobile Intel(R) Pentium(R) III CPU - M  1200MHz
stepping        : 4
cpu MHz         : 797.416

And here is my question, why it only recognises 797 Mhz's when it should be 1200? 

Any help would be much appreciated.

---

### Post by insane_alien on 2006-08-31
your using stepping. to conserve pwer it automatically underclocks when its not under intensive use. in this case it downclocks to 797.416 MHz

---

### Post by Belyel on 2006-08-31
I would look [here]("http://ubuntuforums.org/showthread.php?t=243716&highlight=processor+speed+laptop") for help with that.  It's a common occurance and it's a good thing caused by power management in ubuntu.

---

### Post by zzzname on 2006-09-01
Thank you very much indeed.

---

