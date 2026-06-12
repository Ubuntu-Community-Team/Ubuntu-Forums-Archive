---
title: "Hard Drive Runs Constantly - Why??"
date: 2010-04-21
forum: Hardware
---

### Post by redwoodguy on 2010-04-21
A few weeks ago, this began. My internal hard drive is reading/writing constantly - non-stop, no matter what I am doing. It does it when no applications are running. I tried to see if Process Monitor would should something, but it shows all items are sleeping. 

I fear my hard drive will burn out. It just never stops. 

My system: Ubuntu 9.10
Gateway SX2802: Intel Q8300 with 4GB RAM and a 750GB hard drive. 

Any thoughts here?

---

### Post by cryptotheslow on 2010-04-22
Use the iotop command in a Terminal window to get a real time view of what process(es) are accessing the drive.

---

### Post by redwoodguy on 2010-04-22
Ok, that was helpful. I loaded that and whenever the disk writes a new line appears. Under "command" at the end of the columns, this is the items that keep repeating.

kthreadd
migration/0
migration/1
watchdog/0
watchdog/1
ksoftirqd/3

Now, there are a few others here and there, but those keep coming up every second or two. I notice that BEFORE that column changes to that word - like "kthreadd"  - the word "Firefox" is briefly displayed. Then it switches to "ktreadd." 

Does any of that mean anything? I wonder if I have accidentally set some "preference" somewhere?

---

