---
title: "Can anyone help me interpret this smartctl output?"
date: 2008-08-08
forum: General Help
---

### Post by bobbob1016 on 2008-08-08
I got this output from smartctl, not sure if the drive is failing or not.
[http://pastebin.ca/1095693](http://pastebin.ca/1095693)

---

### Post by Elfy on 2008-08-08
It says it's passed - you can check if there are errors. But I couldn't diagnose a problem from the output if there was one - I just look at the 

> === START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```
sudo smartctl -l error /dev/sd*x*
```wher x = a for disc 1, b for disc2 etc

That will tell you if there are errors logged I believe.

---

### Post by bobbob1016 on 2008-08-08
No errors logged.  I guess I felt that since I was getting "input/output" errors when doing mkdir from terminal via ssh (this is on a server) until after I reformatted, the "Old_Age" and failed previously thing worried me.

---

### Post by sdennie on 2008-08-08
At a glance, those numbers look fine to me.  The Old_Age and Pre_Fail things are a bit unnerving until you realize that they mean that when the numbers drop below the threshold, the disk is either getting old or ready to fail.  The temperature failure seems fairly normal to me as I also have a disk that reports 2 temperatures.  One in the 30-40C range and another in the billions of degrees Celsius range.  The fact that the disk has yet to melt the earth leads me to believe that the latter number is not correct.

---

### Post by bobbob1016 on 2008-08-08
So safe to use or no?  If I understood you, you mean it could fail soon.  It is new, from a new iMac, wouldn't boot anymore, had the folder with a question mark thing, got it replaced with AppleCare.

---

### Post by sdennie on 2008-08-08
It should be safe to use.  The Pre_Fail and Old_Age spam is normal and just means that with a lot of usage (probably years), the disk may begin to fail.

---

### Post by bobbob1016 on 2008-08-09
Ok, I just re-ran one, and checked the log, I got this:
[http://pastebin.ca/1097114](http://pastebin.ca/1097114)

So that would basically mean I have 577 hours or so?  That's about 3 weeks, I know I'm worrying a lot, I just had a few drives fail on me a while back, and I don't want to lose data...

---

### Post by vasiauvi on 2009-09-08
Hello!
Can anyone tell me if I should worry about this errors?
[http://pastebin.ca/1558178](http://pastebin.ca/1558178)

I had a lot of restarts for one year and with this code:
```

sudo hdparm -tT /dev/sda
I get:
Timing cached reads:   766 MB in  2.00 seconds = 382.96 MB/sec
Timing buffered disk reads:  138 MB in  3.01 seconds =  45.79 MB/sec

```

Although this code is saing:
```

sudo hdparm -I /dev/sda | grep SATA
	   *	SATA-I signaling speed (1.5Gb/s)

``` 

The codes are from here :[http://www.cyberciti.biz/tips/how-fast-is-linux-sata-hard-disk.html](http://www.cyberciti.biz/tips/how-fast-is-linux-sata-hard-disk.html)

Thank you and hope to get an answer!

---

