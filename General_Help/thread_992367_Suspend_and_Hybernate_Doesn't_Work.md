---
title: "Suspend and Hybernate Doesn't Work"
date: 2008-11-24
forum: General Help
---

### Post by banana jama on 2008-11-24
hello, i have ubuntu 8.10 install on my laptop a Hp Pavilion dv6000. i've notice when i put the computer in suspend mode and turn it back on only a black screen appears and nothing else. i have to press the pwer button to shut it down. when i put it into hybernate it simply shut down.
  can anyone help me resolve this issue.
   
   P.S.: I've been doing some research and it says that my swap partition is responsible for hybernation (my swap partition is 5 GB). when i start system monitior i notice that it's always on zero. is there anyway to see if my swap drive is enable.

---

### Post by jnorthr on 2008-11-24
go to System>Admin>System Log
which should open up your log file in /var/log/syslog
then you can review messages and syslog entries from the top of the list. you should be able to see the kernel open and use your swap file (or not)

---

### Post by banana jama on 2008-11-24
i don't know i don't see anything about swap. is there any swap only 
MYNAME Laptop MARK
isn't there some command that i can run in terminal that says swap enable swap disable :)

---

### Post by baytuni on 2008-12-06
I had the same problem, then I realized that it was because of my WD 500gb home edition External hard drive which is connected to my computer via firewire. If I unplug it the hibernation and standby modes works just fine.However I am still looking for ways to work it with my external hdd.

---

### Post by banana jama on 2008-12-06
i don't have a external hard drive connected to my laptop though

---

### Post by banana jama on 2008-12-06
o yeah and my swap drive is enable

---

