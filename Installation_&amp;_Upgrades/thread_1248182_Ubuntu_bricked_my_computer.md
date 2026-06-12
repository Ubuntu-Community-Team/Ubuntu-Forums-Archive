---
title: "Ubuntu bricked my computer?"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by jedimattk on 2009-08-23
Here's my situation right now, such as it is. I've had Ubuntu installed for quite some time up until a few weeks ago, when I installed the Windows 7 release candidate on my computer. It has been crashing a lot recently, and got to the point where I literally couldn't even turn it on this morning without it going to the blue screen of death and rebooting. In frustration, I dug out my Ubuntu CD to reinstall it. 

The installer would not complete. The progress bar would get all the way to the end, and then it would just instantly go to a black screen. The CD drive indicator light would then stop flashing. I tried it a few times, then decided to check the disc for defects, which found 1 error. 

So I went off to my other computer, downloaded the ISO, burned it to another disc, and tried again. It eventually loaded the actual install wizard, but it stopped working part way through, saying something like "the file in memory does not match the file on the CD." I had to reboot and scan the disc, which brought up 1 error once again. 

I burned yet another CD with the same iso file, but at a slower speed. It *still* says there is 1 error! I am back where I started now, with the progress bar getting to the end but then stopping abruptly. What's worse, when I try to boot into Ubuntu Live, it gives me a series of errors and then loads a command line interface. 

After all this hassle, I decided to start over, installing Windows XP and then trying Ubuntu again. But no beans; it won't boot from that or any of my other discs. It only loads the Ubuntu CD. 

So ... what the hell do I do now?!

---

### Post by sailthesea on 2009-08-23
You could format the HDD and try again to install XP Ubuntu or 7 It sounds like a drive problem especially as you can live session with ubuntu use that to fix things  then start over Win 7 does not seem to like sharing drivespace with Linux:)

---

### Post by jedimattk on 2009-08-23
Sorry, but I don't know much of anything about command-line Linux. Can I just use the "format C:" command, same as Windows, or is there something else I have to type to get it formatted?

By the way, the errors are a ton of SQUASHFS problems. I am then dumped at the ubuntu@ubuntu:~$ prompt, and have no idea what to do next...

---

### Post by stlsaint on 2009-08-23
you can use the livecd to format your drive...you may have to unlock the drive and swap drive if you have ubuntu installed...

---

### Post by hansdown on 2009-08-23
Hi jedimattk.

download, and burn a copy of DBAN.

[http://www.dban.org/download](http://www.dban.org/download)

It will take a long time, but it will be worth it.

Once it's done, (it may take hours), you can install ubuntu.

---

### Post by jedimattk on 2009-08-23
I downloaded and burned the Boot and Nuke thing. It's auto-nuking my hard drive right now, so I guess we'll just have to see how Ubuntu goes after that.

---

### Post by jedimattk on 2009-08-23
EDIT: Almost immediately after starting, DBAN failed, saying "<0>Kernel panic - not syncing: Fatal exception in interrupt." Now it won't even boot from the Ubuntu CD.

---

### Post by RJARRRPCGP on 2009-08-23
Looks like you probably have faulty hardware or overclocking your processor core(s) too much! 
(or you're required to increase the Vcore for your processor overclock)
 
Did you check the caps for leaking or bulging on the motherboard and power supply?

[http://badcaps.net](http://badcaps.net)

---

### Post by jedimattk on 2009-08-29
Well, my computer has been overheating ever since I added another gigabyte of memory. Maybe the stick was faulty in some way...?

I just removed it and DBAN seems to be running fine now, albiet very slowly. I'm going to erase my entire hard drive and start anew with Ubuntu. However, I will be hard-pressed to ever run Windows 7 on here now with only 512MB of memory. I think this computer will remain an Ubuntu box forever; I'll wait for my new Inspiron later this year to run Seven.

---

### Post by hansdown on 2009-08-29
Glad you sorted things jedimattk.

DBAN does take some time.

Good luck.

---

