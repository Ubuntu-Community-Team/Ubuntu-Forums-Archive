---
title: "displaydetection doesn´ t work anymore"
date: 2015-05-20
forum: Hardware
---

### Post by Royke on 2015-05-20
Hello Ubuntero´s,

A few weeks ago my second display suddenly showed nothing but grey lines and just a little desktop. It was after some kind of update. This is the case: 

The main display is a philips hd tv with support for a 1920x1080 res. The other one was just an old 4:3 flatscreen with just a res. of 1024x768 but it was perfect for with my dj-gear. The driver used is the x.org-video-radeon, the open-source one. But when the grey lines occured i tried the both catalist ones. Now i am verry sorry that i did that because the X.org driver says i have a default monitor with a max res. of 1400x...:cry: I tried many things. First of all i removed the outdated display and i will keep it like this. Also purging the driver and removing xorg.config and even copying the entire X11-folder from my backupsystem. None of it gives the ID back. Maybe the problem is that i also tested the other catalist, updates driver and that not everything is purged?
In almost a thousand ways i searched the net and i found no one with the same issue, nor a clear explanation how it works. Only outdated help. Also the official X.org help showes me nothing useful to me. Isn´t there just a simple package that does the display-setup from scratch? 

Please help, any info on this would help. It is my productionmachine for my music-related stuff and i´m getting behind. 
A 46inch tv is not a default-monitor if you ask me, maybe in the near future:guitar:

---

### Post by Royke on 2015-05-21
Wow, a day later and still no answer to my question. This is the first time since 2007. Maybe it's not good to have me around Ubuntu so little and i need to interfere more, because this forum always was one of the best of the world and i proberbly can help keeping ubuntu easy to use. If it takes a few days more, maybe i'll post the sollution myself.;)

---

### Post by v3.xx on 2015-05-21
Not many old-timers in the forum :)

You got a tough question
Here's how I see it:
I think dual monitors are common, but add radeon/catalist and your in a small group of users.
I help when I can, but I usually limit my replies to GeForce.  Thats what I run.

Good luck

---

### Post by Royke on 2015-06-29
Today i fixed it with just uninstalling all amd-packages trough synaptic and the funny part was that i didn't even had to reboot to activate the open driver again with the right detection. This proves that purge is not a great way of completely removing in this case.

---

