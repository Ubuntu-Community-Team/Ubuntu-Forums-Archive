---
title: "Mouse moves randomly"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by cubix on 2006-06-03
Hi!

Computer: Dell Latitude

Problem: Quite frequently the mouse moves at random and even do clicks. Had this problem in the version before 6.06 too. The solution then was to change an if condition in a file so the condition looked like the condition above in the file. 

Problem is i cant remember what file it was! Know this sparse info is not much to work with but crossing my fingers. If it is of any help, It was not the change IMPS/2 to PS/2 or disabling the touch pad solutions.

---

### Post by cubix on 2006-06-04
Found the solution. It was in /usr/share/powernowd/cpufreq-detect.sh
Changed it so it always load PIII_MODULE=speedstep-ich.

---

### Post by crobruncato on 2006-06-06
I"m still having this problem with an IBM r31. I got an older version of ubuntu to work a while back, but dapper is giving me grief. I tried your powernowd solution, and it's not working for me. Any other ideas?

Thanks all,
Rob

---

### Post by brn on 2006-08-03
Thanks!  I had exactly the same problem with my Dell Latitude.  This fixed it.  Although it is doubtful that I will live long enough to discover all the nooks and crannies lurking in Linux, I am really grateful that this forum is here to help and sustain.

---

### Post by yukito on 2006-08-03
> **crobruncato said:**
> I"m still having this problem with an IBM r31. I got an older version of ubuntu to work a while back, but dapper is giving me grief. I tried your powernowd solution, and it's not working for me. Any other ideas?

Thanks all,
Rob

I have had similar problems with my now dead Acer Aspire 1357LMi in the past, and the problem seems to be heat related. Since touchpads react to the heat of your fingertips, using the touchpad in the heat or cold can make it behave odly. Also, if you have any hot peripherals around the touchpad (in most cases the HDD is near it), those can cause this behaviour as well when they are used a lot. There's no solution for the problem if it's your hard drive causing the problem I'm afraid. I've had the problem with several notebooks (every single one I used except for a powerbook G3 and this sony vaio, which is only a few days old so the problem could still show up later)

Don't know if it's the same problem, but it sure sounds similar.

---

