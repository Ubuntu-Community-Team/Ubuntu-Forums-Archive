---
title: "Hard drive too hot in ubuntu"
date: 2008-08-28
forum: Hardware
---

### Post by pranithkumar on 2008-08-28
Hello,

I'm running hardy on a dell xps m1330 with 250gb hard drive. To fix the load_count_cycle issue i used a -B value of 254 and the load count does not increase any more for me. But i think this is making the hard drive too hot as I can feel the heat near the palm rests. With smartctl i got the temperature as 42 degree C. Is this normal?

How do i reduce the temperature of the hard drive? What is the good value for hdparm -B? (I think 254 is bad because this does not do any power management. I can bear upto 10-15 load cycles per day if it keeps my hard drive cool.)

Thanks,
Pranith

---

### Post by jongkind on 2008-08-28
42 deg.C is OK. 

Here is an interesting Google document about failure statistics of harddisks. 

[URL="http://labs.google.com/papers/disk_failures.pdf"]
http://labs.google.com/papers/disk_failures.pdf[/URL]

Paragraph 3.4:* "In fact, there is a clear trend showing that lower temperatures are associated with higher failure rates. Only at very high temperatures is there a slight reversal of this trend."* Also surprising is that the use of the disk during the first 6 months strongly affects its reliability for the remainder of the lifespan.

---

### Post by funnylife_ma on 2008-09-15
Hi there,

I have an ASUS A6VA with Fujitsu HardDrive, and for usual work, the temperature is higher than 50°C. I am using Hardy Heron.

Thank you in advance for any answer.

---

