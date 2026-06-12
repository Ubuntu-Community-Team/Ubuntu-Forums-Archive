---
title: "ubuntu 8.10 + ati 4650"
date: 2009-09-18
forum: Hardware
---

### Post by wachrno on 2009-09-18
Hi
I've been trying to install ubuntu 8.10 on my laptop but it simply doesn't start the X. My pc has an ati 4650 i don't know if that's what causes the problem but is there any incompatibility with this graphics card? Does anyone knows how to solve this?
Thanks in advance
Regards

---

### Post by Zoot7 on 2009-09-18
Try following the guide here:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

It's this procedure i've used to get my HD4870 up and running, and also to get the mobile 3450 drivers up and running.

---

### Post by wachrno on 2009-09-18
But this is done after installing ubuntu right? The problem is that i run the live CD and it appears the normal screen: run as live cd, install ubuntu,.... but whether i chose the first or the second it doesn't even start the X i have the errors and then the shell appears and if i want to install ubuntu i have to do that manually through the shell (unfortunality i don't know how to do that :P) is there a way to do that without using the shell?
I already have ubuntu 9.04 is there a way to downgrade keeping the drivers for the graphics card?(don't know but this is probably a stupid question)

---

### Post by Zoot7 on 2009-09-18
Okay I'm not sure I understand.

You run the liveCD and install Ubuntu, but upon rebooting after the installation is finished, X won't start? But it works okay while running off the liveCD?

---

### Post by wachrno on 2009-09-18
nop i can only see the first screen as in the one where you choose the language and where are the options run without installing(i don't remember the exact words), install ubuntu, check for error, and more which i don't remember. If i choose the first( run without installing) or the second(install ubuntu) it will start as usual with the progress bar but then a lot of errors pop and X won't start. After this i have the shell open no ubuntu installed. Any idea?

---

### Post by Zoot7 on 2009-09-18
Sounds like there's a problem with the liveCD, you might want to try checking it for defects and maybe downloading it again.

And no, to my knowledge there isn't a way to downgrade to an earlier distribution. The only option is a re-install. 
BTW if you're not too fond of upgrading every 6 months your best bet is the LTS editions. I'm still using Hardy on several of my machines, and Hardy is what's going to stay on them until 10.04 comes out.

---

### Post by wachrno on 2009-09-18
hmm i'll try to install 8.04 but probably if 8.10 has an incompatibility problem won't 8.04 have it too? I just don't keep 9.04 because i need an earlier version of python an even if i download it the newer version still has some kind of an issue with pythonQt... so i was trying to install 8.10 in a new laptop...but well i'll try 8.04

---

### Post by Zoot7 on 2009-09-18
> **wachrno said:**
> hmm i'll try to install 8.04 but probably if 8.10 has an incompatibility problem won't 8.04 have it too?
I don't think it's an incompatibility, the liveCD boots, and installs on everything perfectly from what I've found over the last 3 years.
I'd say the problem is more likely a corruption caused during downloading or something similar. Checking it for defects is the thing I'd do.

---

### Post by wachrno on 2009-09-18
ok i could install 8.04 it just didn't recognise the wireless card i'll try again with 8.10... i'll download it again the errors check didn't give me any error

---

### Post by wachrno on 2009-09-19
ok i think 8.10 really doesn't like my laptop i've download both 32 and 64 version and checked for errors on both cd's. No errors. And then tried to install both of them and it simply goes to the shell... anyone have any idea?
Thanks

---

### Post by Zoot7 on 2009-09-19
Strange, TBH I've no idea, Why not give the alernative install CD a shot?

Also, if you're dependent on an old package, why not just stick with 8.04?

---

### Post by wachrno on 2009-09-19
Already done that :P. With the alternate CD i successfully installed ubuntu 8.10 but when i rebooted it i had the same problem the X didn't start

---

