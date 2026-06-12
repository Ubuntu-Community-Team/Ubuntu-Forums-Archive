---
title: "Problems with installing Java!"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by MindFusion on 2009-09-29
Hi all, this is my first post here in the Ubuntu forums. After 2 years of pointless agony having a windows vista (cancel or allow? AAAAAAARGH) i decided to install Ubuntu on my HP laptop, 4 gig RAM, Nvidia 8400m, 2,1 Mhz processor, 64-bit AMD Athlon X2. I love it! Unlike what most people would say, linux is visually more enhancable thshut an any kind of windows os so far, and using the terminal to install stuff is just plain cool. I have been having a hard time getting all the commands though ...

Just a half an hour ago i tried installing java using my terminal (sudo apt- ...). However, i minimized the terminal and when i opened it again, there was a screeen for me to accept the java agreements, with YES as only option. Now normally, this would be in red, so i could press enter, but i couldn't do anything. I pressed enter a couple of times and nothing happened, still. I then shut down the terminal, but when i tried to enter the code again to install java, i got an error report. 

Does anyone know how to undo all the java installing so i can re-install the app?

Thanks in advance!

---

### Post by earthpigg on 2009-09-29
hi,

i vaguelly recall some similar silliness some years back.

try synaptic.

i think the package name, if you just want to play web-based games in java, is 'java-jre' or maybe 'sun-jre'

---

### Post by credobyte on 2009-09-29
You got an error because aptitude was brutally terminated ( by closing the terminal window ).
Restart your PC and execute the same command ( apt-get thingy ). When you see a blue screen ( in terminal ), hit TAB / ENTER ( the same for license ).

---

### Post by MindFusion on 2009-09-29
Ehm, excuse me for the noobyness, but i do not understand what do really.

I rebooted my pc and entered the code again but this is what i got.

> jakob@MindFusion:~$     sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
[sudo] password for jakob: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


---

### Post by credobyte on 2009-09-29
Run:
```
sudo dpkg --configure -a
```

---

### Post by MindFusion on 2009-09-29
jakob@MindFusion:~$ sudo dpkg --configure -a
[sudo] password for jakob: 
Processing triggers for man-db ...
Setting up odbcinst1debian1 (2.2.11-16build3) ...

Setting up unixodbc (2.2.11-16build3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


so now i can retry it?

---

### Post by credobyte on 2009-09-29
> **MindFusion said:**
> 
so now i can retry it?

Yes.

---

