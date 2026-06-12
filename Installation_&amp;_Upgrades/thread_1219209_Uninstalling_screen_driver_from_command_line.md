---
title: "Uninstalling screen driver from command line"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by zcacogp on 2009-07-21
Chaps, 

Long story cut short ... 

- I installed kernel 2.6.30 on my desktop machine, as described in this thread here: 

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

- This broke the machine - the login screen was messed up, and unusable. 

- I wiped the install and re-installed from the CD. 

- I re-installed the 2.6.30 kernel, and it worked fine. I was about 95% of the way through installing everything I wanted on the machine, when ... 

- I installed the same screen driver as I had originally, re-booted, and the login screen was messed up again. 

So now I have a machine which will boot to a command line, but won't boot fully into Ubuntu. Seemingly because there is a conflict between my screen driver and the 2.6.30 kernel. 

The graphics card I have is on-board the motherboard, and it's an ATI Radeon HD 330 card, and I *think* the screen driver that was installed was a fglrx one. (It was selected automatically and listed as 'no enabled'. I clicked on 'enable this' and re-started, and the problems as described above re-started ... ) 

So, my question. How do I change back to the original screen driver from the command line? OR how do I change back to the original kernel from the command line? Either will do ... 

Thanks, in advance, for any help anyone can offer. For what it's worth, when I ruined the first installation I posted this thread here: 

[http://ubuntuforums.org/showthread.php?t=1214868&page=3](http://ubuntuforums.org/showthread.php?t=1214868&page=3)

Oh, the install is 9.04 Jaunty. And I'm a bit of a beginner (rarely venture out of "Absolute beginner talk", so please talk slowly ... thanks!) 


Oli.

---

### Post by mudcat on 2009-07-21
boot to recovery mode; sign in as root; and then sudo apt-get remove the driver that caused the problem

---

### Post by zcacogp on 2009-07-21
Mudcat, 

Fab! Thanks - that sounds simple. 

How do I know what driver it is? Is there any way I can get the system to display the screen driver it is using? 

(That question may reveal just how much of a beginner I am. Apologies ... and thanks.) 


Oli.

---

### Post by zcacogp on 2009-07-22
Got it. It was this: 
```

sudo apt-get remove --purge xorg-driver-fglrx
```

... from here: 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Thanks for your help. 


Oli.

---

