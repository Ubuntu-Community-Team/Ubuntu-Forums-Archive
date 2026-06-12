---
title: "Defragmenting windows from linux"
date: 2008-11-09
forum: General Help
---

### Post by davideotape on 2008-11-09
I am currently running a dual boot system, with ubuntu on one hard drive and windows on a completely separate hard drive. At the moment, my defrag software on windows will not defragment some files because they are in use by the OS. Is there any software that would allow me to defragment my windows hard drive from Ubuntu?

---

### Post by philinux on 2008-11-09
All you need to do is schedule the defrag for the next startup of windows.

---

### Post by davideotape on 2008-11-09
Yes, but if I defragment in Linux I can also use the OS at the same time, which I would prefer.

---

### Post by ronnielsen1 on 2008-11-09
I don't think you can use linux for this but I may be wrong. You might want to check out 
[defraggler ]("http://wlmtips.com/2008/07/16/defrag-your-hard-drive-with-defraggler-windows-wednesday/")

---

### Post by davideotape on 2008-11-09
That's the software I'm using atm on windows, but it won't run on linux

---

### Post by lukjad on 2008-11-09
Doing something like defraging a hard drive from one OS to another is not a good idea. It is also not a good idea to scan and remove viruses and infected files from Linux to a Windows partition. Things just don't seem to work out well.

---

### Post by ajgreeny on 2008-11-09
When I used windows I always defragged in safe mode after disabling the virtual memory.  I haven't used it for so long now that I can't remember how I did the latter, but I think I right clicked on "My Computer" on the desktop and got to it that way.  This way meant that only the very minimum of services were running and there was no "swap" file which could not be defragged to worry about.  It still took an age to do, however, so I'm very glad it's not needed in ext3 file systems.

---

### Post by davideotape on 2008-11-11
Yes, that is one of the reasons I have migrated over to linux. The only reason I still use windows is to play games on it. I have tried using wine, but I have found that most new 3d games don't work that way. (although luckily peggle works!)

---

### Post by lukjad on 2008-11-11
> **davideotape said:**
> Yes, that is one of the reasons I have migrated over to linux. The only reason I still use windows is to play games on it. I have tried using wine, but I have found that most new 3d games don't work that way. (although luckily peggle works!)
Well, glad to hear that. The thing is that it is better to just defrag while in Windows. Just choose a day you are going out, start the defrag and let it run.

---

