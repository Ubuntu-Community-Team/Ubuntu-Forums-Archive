---
title: "Computer start swapping and becomes unresponsive"
date: 2005-11-26
forum: General Help
---

### Post by jonatan on 2005-11-26
Hi

I'm a very happy user of Ubuntu 5.10. I have a problem on my laptop though (HP nc6120):

Every now and then, for apparently random reasons, the computer start heavy swapping. After a while the computer becomes totally unresponsive and the sound stop etc. It is like that for ~5 minutes or more and then (presumably when swap is full) it goes back to normal.

This happens seemingly random: just yesterday it happened to me when I clicked an URL in Evolution, when I played a video with Xine and when compiling a C++ program. When I repeated the operations there was no problem.

Does anyone else have this problem? I could not find any posts about it here. Also it's quite hard to debug: i try, before the computer becomes totally unresponsive, to start 'top' and sort by memory, but I've not managed to get any useful information before the computer freezed so far. And when it goes back to normal the memory usage is of course back to normal as well ...

---

### Post by kosmic on 2005-11-26
Hum it looks like it is some Cron Jobs that starts running in the background, just deactivate the cron jobs

---

### Post by jonatan on 2005-11-26
Well, I have this feeling that it doesn't happen until I do *something*, clicking an url, running make etc. It never happens when the machine just sits there and plays music for exmple.

And I have no exotic entries in cron, just the usual slocate, sysklogd, etc. I do however have beagle installed, which has a crontab entry, but I don't use beagle. Also, it's configured to run once daily, and this can sometimes happen three times in an hour. I have no tasks scheduled in cron.hourly.

---

### Post by LeSkip on 2005-11-26
I can attest to this happening. There seems to be problems with the priorities which lets the kernel use all the processor time for swapping memory, and lets absolutely no time for gnome. This is a serious problem when you have a program running amok. 

A concrete example: I have had a memory leak in one of the systems i use for my thesis that consumed about 100 MB per minute. This is quite alright until I have filled my 1 GB. Once I am past the point where it starts swapping, the only way to halt is to pull the power plug. I have tried waiting more than two hours, but to no avail.

---

### Post by jonatan on 2005-11-26
Decrease your swap partition ;)

---

### Post by jonatan on 2005-11-26
Ok, I apologize, I must have been both blind and stupid: I found out that I had no swap partition mounted! No wonder it went down under heavy load...

---

### Post by Treviño on 2005-12-15
Same here... My partition is full and the kernel priorities desn't seem to work... A process take all and it's impossible to kill it... I've lost an important mail for it :(
My swap is about 1.2GB and I've 512MB of RAM, I think it's enough, but sometimes it's impossible to use the PC.

Do you have idea why? Do you think that upgrading to the new kernel 2.6.14-xx could solve the problem?
Thanks!

---

