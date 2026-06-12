---
title: "CPU nearly always at &gt;90% recently"
date: 2008-07-18
forum: General Help
---

### Post by Crusty Juggler on 2008-07-18
My system has recently (over the last week) been very sluggish and the CPU is nearly always maxed out.  I generally have Firefox, Thunderbird and OOo3 Beta running, and maybe a couple of PDFs with evince, but even when I am only internet browsing, it will often grind to a halt.  

I'm only working with a 1.5 GHz Celeron with 1 GB ram, but this has worked fine for months.

Any suggestions?

---

### Post by TSJason on 2008-07-18
application management?
:popcorn:

---

### Post by Zack McCool on 2008-07-18
Can't really give advice until you let us know what is hogging the cpu...

From a terminal, run top (or install and run htop) and see what the top few cpu users are.  Let us know what they are, and how much they are hogging...

---

### Post by Crusty Juggler on 2008-07-19
top shows firefox using about 45% CPU, Xorg using about 40-45%.

---

### Post by steveneddy on 2008-07-19
Try reinstalling Firefox and turning off Compiz.

---

### Post by unc0nn3ct3d on 2008-07-20
[http://ubuntuforums.org/showthread.php?t=855508](http://ubuntuforums.org/showthread.php?t=855508)

we're talking about what is most likely the culprit in that thread right now.  Go get Adblock and NoScript addons for firefox or just shut FF down while you are doing something else

---

### Post by steveneddy on 2008-07-20
I had an issue a while back, after the reinstall of Hardy, where I had high CPU usage.

Cairo Clock and Beagle Tracker were the problems for me. Cairo would switch places with X while running **top.**

---

### Post by lukjad on 2008-07-20
I think that the culprit may be the System Monitor. I read somewhere that it has a memory leak that hogs the CPU. Also, Firefox 3.0 does sometimes hog the memory, I think that there may be a fix to that, or you could just backgrade to Firefox 2.0

---

### Post by steveneddy on 2008-07-20
I would turn off/disable one thing at a time until the CPU usage subsides. If it is Firefox I would turn off services one at a time in Firefox until CPU usage goes down.

---

### Post by Julian David Pitt on 2008-07-20
I seem to have the same issue with FF hogging some 80% of the cpu, I have tried disabling the extensions one at a time but as of now I still have no idea what is causing this.

---

### Post by Crusty Juggler on 2008-07-22
I added NoScript to Firefox and it helped a little bit, but I found myself often enabling scripts on my favourite sites, thus defeating the purpose.

However, I just disabled the Yahoo Webmail add-on in Thunderbird and it seems to have solved my problem.  It's disappointing that I can't use Thunderbird for Yahoo, but my computer works normally again.

---

