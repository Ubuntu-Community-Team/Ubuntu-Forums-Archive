---
title: "i8kutils unable to set fan speed in Dell Inspiron 1525"
date: 2015-03-04
forum: Hardware
---

### Post by Claudio81 on 2015-03-04
Hi everyone
I'm running Ubuntu Trusty on my Dell Inspiron 1525.
I installed i8kutils following this tutorial:
[http://keenformatics.blogspot.co.uk/2013/06/how-to-solve-dell-laptops-fan-issues-in.html](http://keenformatics.blogspot.co.uk/2013/06/how-to-solve-dell-laptops-fan-issues-in.html)
It works fine for showing the fan speed but completely unable to set the speed:
```
claudio@claudio-Inspiron-1525:~$ sudo i8kfan - 1
0 0
```
or when I'm running "sudo i8kmon" with a threshold of 40 for testing purposes:
```
temp, left, right, ac state: 49 0 0 0
# exec /usr/bin/i8kfan {} 1
temp, left, right, ac state: 52 0 0 0
# exec /usr/bin/i8kfan {} 1
temp, left, right, ac state: 51 0 0 0
# exec /usr/bin/i8kfan {} 1
temp, left, right, ac state: 55 0 0 0
# exec /usr/bin/i8kfan {} 1
temp, left, right, ac state: 54 0 0 0
# exec /usr/bin/i8kfan {} 1
temp, left, right, ac state: 54 0 0 0
# exec /usr/bin/i8kfan {} 1
temp, left, right, ac state: 55 0 1 0
temp, left, right, ac state: 54 0 1 0
temp, left, right, ac state: 51 0 1 0
temp, left, right, ac state: 52 0 0 0
# exec /usr/bin/i8kfan {} 1
temp, left, right, ac state: 52 0 0 0
# exec /usr/bin/i8kfan {} 1
temp, left, right, ac state: 53 0 0 0
```

you can see the daemon completely helpless until the usual something else does the job.
I updated the bios and researched everywhere on the net.
I'm really curious about one thing:
what has been controlling the fan all this time, before i8kutils, and still is today?

---

