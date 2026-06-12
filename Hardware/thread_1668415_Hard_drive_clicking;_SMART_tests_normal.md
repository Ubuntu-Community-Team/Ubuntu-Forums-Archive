---
title: "Hard drive clicking; SMART tests normal"
date: 2011-01-16
forum: Hardware
---

### Post by 3602 on 2011-01-16
So my computer (see sig) hard drive has been clicking since the day I got it. I tried to run SMART tests through the Disk Utility.
I had three choices. Short, Complete and Conveyance. The short test came back as Disk is healthy with zero bad sectors. The Complete test will not run as the progress bar does not advance one bit. Nothing happens when I choose Conveyance.
Drive is a Hitachi ATA HTS725050A9A364.
Here's some data if it can help:
> Read Error Rate - 0
Throughput performance - N/A
Spinup time - 2msec
Start/Stop count - 35
Reallocated sector count - 0
Seek error rate - 0
Seek timer performance - N/A
Power-on hours - 2.5 days
Spinup retry count - 0
Power cycle count - 0
Attribute 183 - N/A
End-to-end error - 0
Reported Uncorrectable errors - 65536
Command-timeout - 43
Airflow temperature - 40°C 104°F
G-sense error rate - 0
Power-off retract count - 262148
Load/unload cycle count - 242
And everything below is zero.
So is my drive dying or it's the HP ProtectSmart (whatever that is) acting up? I read somewhere that "this is a problem with all HP Pavilion portable computers". Is this true?
Thank you very much.

---

### Post by jcolyn on 2011-01-16
Does it click constantly or only when you open/close program and are browsing etc?

---

### Post by 3602 on 2011-01-16
Not all the time. Most of the time it's soft buzzing (like a normal hard disk during read/write). It sometimes clicks (rarely) when I open a webpage or Software Center.
The most clicking was yesterday, when I watched a bunch of videos on the Tube (it can click for like 10 times before a new video loads). Then I stopped and chatted instead for hours, no clicks during chat.
I'm running a Complete test as of now, I thought maybe I should let it run for a bit more before cancelling.

EDIT: OK the bar just advanced. Good.

---

### Post by IcarusR on 2011-01-16
Make sure you do regular backups just in case it does fail.

---

### Post by Kedrin on 2011-01-16
If you are running a "complete" test cycle, let it go through at least one permutation else the test will only tell you the results of the beginning of the test.  It sounds as though the read/write seek is over actuating and the drive will eventually fail.  You will likely experience difficulty booting and may find yourself tapping the drive to get it to spin (an** "old server"** trick for old servers).

At the very least, follow the previous advice and BACKUP that which you can't afford to or simply don't want to lose.  The END IS NEAR

---

### Post by jcolyn on 2011-01-16
> **3602 said:**
> Not all the time. Most of the time it's soft buzzing (like a normal hard disk during read/write). It sometimes clicks (rarely) when I open a webpage or Software Center.
The most clicking was yesterday, when I watched a bunch of videos on the Tube (it can click for like 10 times before a new video loads). Then I stopped and chatted instead for hours, no clicks during chat.
I'm running a Complete test as of now, I thought maybe I should let it run for a bit more before cancelling.

EDIT: OK the bar just advanced. Good.

Most laptops are noisier than a desktop mainly due to the small cramped size. My experience with HP laptops has been they tend to be noisier. I can hear my Dell laptops but not my desktop.

The clicking of hard drives is for the most part normal so unless you are experiencing issues such as slow bootup etc I wouldn't worry..

---

### Post by 3602 on 2011-01-16
Complete test completed OK: Disk is healthy. Values unchanged.
I do backup my stuff (ain't much really), boot is fast as ever (also shutdown).
So you're saying that HP portable computers do click a bit? Well SMART came back normal so I should stop worrying, huh.
Thanks.

---

### Post by jcolyn on 2011-01-16
I wouldn't worry..

---

