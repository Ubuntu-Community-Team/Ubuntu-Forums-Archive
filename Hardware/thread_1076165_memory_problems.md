---
title: "memory problems"
date: 2009-02-21
forum: Hardware
---

### Post by Pitboss on 2009-02-21
Hi I'm a newbie and I have this strange problem with my pc memory. From time to time the memory usage increases significantly, even if I don't start any new programs. I tried to monitor it with top, and sorted the results by memory to see something strange. Even if the memory in use is nearly 80% of my 2GB ram, the percentage of programs in %MEM column doesn't sum up even to 35%. After time, the memory usage drops 30% in an instant (randomly I guess, I don't close any programs in this moments) and my pc freezes for some milliseconds. I'm thinking of memory leaks but I don't see any with top.

So any idea what the hell is going on?

---

### Post by lloyd_b on 2009-02-21
Open a terminal window, and type "free".  You'll get a report something like this:
```
lloyd@dell:~$ free
             total       used       free     shared    buffers     cached
Mem:        512604     505292       7312          0      21480     198216
-/+ buffers/cache:     285596     227008
Swap:       979956       1788     978168
```

The number to pay attention to is in the "used" column, after the "-/+ buffers/cache" (285596 in this case).  This tells you how much memory is available, after subtracting whatever is being used for buffering/caching.

Linux will, by default, attempt to use ALL of your memory.  Which means that if you aren't using it for programs, it'll try to fill it up with disk cache.  If all of your memory is "used", when a program requests memory, the system will automagically free up some of this cache.

Lloyd B.

---

### Post by Pitboss on 2009-02-21
> **lloyd_b said:**
> Linux will, by default, attempt to use ALL of your memory.  Which means that if you aren't using it for programs, it'll try to fill it up with disk cache.  If all of your memory is "used", when a program requests memory, the system will automagically free up some of this cache.

Many thanks, Lloyd B., for your fast answer. This explains a lot. I knew about the free command, but what it gives is basically what I get in the upper part of the terminal, when I type top. What I wanted to know, was why eventually ALL of my memory gets in use. Now I know.

Pitboss

---

### Post by Pitboss on 2009-02-21
However, I checked one more time, and this time I'm pretty sure that this is no ordinary linux behaviour, since if I turn off all the running programs memory usage by programs is 50% and raising. Perhaps this is some linux module memory leak, but I'm not sure enough how to get the memory occupied by modules.

---

### Post by binbash on 2009-02-21
Dude this is normal, windows and linux has different ram managements, at the moment i am running firefox with 5 tabs open and one software and i am using 2gb memory.You are thinking windows way.

---

### Post by Pitboss on 2009-02-21
No, I tell you man, I'm not joking around. I believe I found the problem however. It was fglrx - the ATI proprietary driver. There is a new one from yesterday so I'll try it. ATI I #&$%^#@ hate you.

I just checked the new driver, seems to behave this way also. I reported it.

---

