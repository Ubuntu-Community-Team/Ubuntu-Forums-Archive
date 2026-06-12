---
title: "Need an up to date ssd how to on 11.04"
date: 2010-12-13
forum: Hardware
---

### Post by grimmson on 2010-12-13
Sorry guys, I'm being lazy. Searched the forums for ssd 11 and came up with **** butkus. A zillion pages dating to 2008. Anyone have a proven plan for ssd with trim support (and other tips) for Narwhal?

P.s. Ive seen Jackalope, two headed snakes and an albino dolphin. What is a Natty Narwhal? Or should I just google images? 

Thanks.

---

### Post by w1ll1am on 2011-02-22
Not sure if everything is going to be the same in 11.04 I am running 10.10 on an OCZ SSD. 
I am using the second link in this post and I have trim working. I have had my SSD in my Dell Inspiron Duo for almost a month. Here are my results for 

```
 sudo hdparm -t /dev/sda 
```704 MB in  3.00 seconds = 234.47 MB/sec


[http://ubuntuforums.org/showthread.php?t=1612240](http://ubuntuforums.org/showthread.php?t=1612240)

Hope this helps

---

### Post by donalgodon on 2011-03-27
/dev/sda:
 Timing cached reads:   6360 MB in  2.00 seconds = 3181.18 MB/sec
 Timing buffered disk reads: 592 MB in  3.00 seconds = 197.18 MB/sec

---

