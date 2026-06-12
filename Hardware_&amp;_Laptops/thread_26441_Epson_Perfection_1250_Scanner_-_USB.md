---
title: "Epson Perfection 1250 Scanner - USB"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Staesys on 2005-04-12
It's detected and everything looks good, but when I go to scan something, the scanner makes a "chuncking" noise like it's firing up to scan and then...nothing. I know this scanner works, as it was working on windows xp pro just before I installed Ubuntu.

Thanks!

---

### Post by jeremy on 2005-04-16
It sounds like you have the same problem as I do with my Epson 1200 Photo.
[http://ubuntuforums.org/showthread.php?t=24755](http://ubuntuforums.org/showthread.php?t=24755)

---

### Post by kleeman on 2005-04-16
Here is a howto for this scanner in Mandrake. 

[http://daniel.fiser.cz/?go=epson1250](http://daniel.fiser.cz/?go=epson1250)

One thing I noticed is you can set the warmup time in the file 

 /etc/sane.d/plustek.conf

(this was suggested in the other thread mentioned above)

---

### Post by Staesys on 2005-04-20
Thanks guys, I appreciate it. Setting the Warmup to 5 worked for me. The scanner now starts up scanning almost imeadiately.

:-)

---

### Post by Staesys on 2005-04-21
Okay, new problem... When scanning at 72 DPI, everything's fine, but when I scan at 300 DPI, I get lines through the picture where the scanner paused in the scanning process. In other words, it seems to be loosing data while it pauses to send the scanned information to the computer. Either that or the positioning of the scan head is off when it starts back up.

The computer was running Windows XP Professional before and I had no problems scanning on it with this scanner, so I'm sure it's just a tweak or something...

Any ideas?

----------------------------------------

Computer Info:

Ububuntu 5.04
AMD K6-II 450MHZ
328 MB / RAM

Scanner:

Epson Perfection 1250U (USB)

---

### Post by Seq on 2005-04-21
Actually, I had to do some scans monday night and grabbed my friend's 1250, and this thread was my main resource to get it working.

However I noticed the same issue, but I believe I could scan at 300 without issue (i think it was setting to 400+ that caused the problem).

I'm in exams and doing final projects, so I haven't had time to investigate.. :(

---

### Post by derfinsterling on 2007-03-12
Thanks! The warmup thing worked for me as well!

---

