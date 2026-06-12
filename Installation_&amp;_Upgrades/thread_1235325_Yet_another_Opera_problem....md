---
title: "Yet another Opera problem..."
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by horrorpunk138 on 2009-08-08
Ran with Opera for the longest time, until today when it just pooped out and refuses to load. After random attempts, I've broken down and tried uninstalling it all together, with a re-installation.

I've tried installing from Synaptic, as well as a straight download from Operas site. I've tried the static, (9.64) as well as the newest versions (10.00b1 and 10.00b2, I WAS using 10.00b1 for a few months).

Here's the problem. Computer shows it's installed, and if I try to open it, the "border" comes up for a second, like it WANTS to load, but nothing happens after that.

I'm using Jaunty, and just let me know anything else I need to post.

Thanks in advance.

---

### Post by Arup on 2009-08-08
Do a sudo-apt-get --purge remove opera Open up your home folder and do ctrl+h to show hidden files, delete .opera folder. Reinstall Opera from the deb file you downloaded and see what happens.

---

### Post by horrorpunk138 on 2009-08-09
Did that, yet got the same results. Trying to open it with terminal (opera %u) gives me this...

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/rob/lib/opera/10.00/opera: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by horrorpunk138 on 2009-08-09
And according to Synaptic, my "libstdc++.so.5" package/file just disappeared.

After having Synaptic re-install that, Opera comes up, with all my settings gone, but oh well. I'll say it, I HATE FireFox.

Thank you

-rob

---

### Post by darco on 2009-08-09
Chromium , my friend...you will never look back :)

darco

p.s. Opera 10b2 is my backup...runs great

---

### Post by TheNosh on 2009-08-09
> **darco said:**
> Chromium , my friend...you will never look back :)

darco


not true of everyone, i have chromium, and to give it a fair shot i used it exclusively for about a week (after flash started working) and i still prefer opera. chromium is still my secondary browser and firefox is third.

to each his own i suppose

---

### Post by darco on 2009-08-09
True...
with Chromium its a little tougher if you have a 64bit OS as you need to use a x32bit flash player. Once they develop the 64bit version I feel it will be on top....
Opera 64 is awesome too!. I love the fact the I can use my left/right scroll key to go back and forth on webpages!
I turned my back on FF once they release their latest version but neglected their x64bit  users (tracemonkey non-functional)

darco

---

### Post by TheNosh on 2009-08-09
> **darco said:**
> I turned my back on FF once they release their latest version but neglected their x64bit  users (tracemonkey non-functional)

darco

i haven't quite turned my back on firefox, but it's just because i'm addicted to stumbleupon. there are a few methods of sort of getting it to work in opera, but the functionality isn't quite the same.

---

### Post by chrisme52 on 2009-08-10
Opera10 beta 2 runs mint on my dual core ibex but slow and buggy on my single core jaunty?

---

