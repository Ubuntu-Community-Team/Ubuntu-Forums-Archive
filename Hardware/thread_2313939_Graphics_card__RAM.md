---
title: "Graphics card / RAM"
date: 2016-02-17
forum: Hardware
---

### Post by extremis11 on 2016-02-17
Hi all!

What is the filesystem location where information about graphics card and RAM is stored? If i install another graphics card with exactly the same chipset (but from different vendor) will it use the same driver(s) / configuration file(s)? What about memory modules of exactly the same size but different frequency? Are these things determined automatically on boot time?


Thanks,
Kostas

---

### Post by mörgæs on 2016-02-17
If you run **sudo lshw > lshw.txt** you will see all hardware information in the file lshw.txt.

You can swap graphics card freely if you use open source drivers. Closed source drivers need a little more adjustment.

Memory modules do not have to be of the same speed. The system chooses a speed suitable for all modules.

---

### Post by gordintoronto on 2016-02-17
+1

If you would like the hardware information nicely formatted, use this command:
sudo lshw -html > lshw.htm

---

### Post by extremis11 on 2016-02-18
Thank you all for your support!

---

