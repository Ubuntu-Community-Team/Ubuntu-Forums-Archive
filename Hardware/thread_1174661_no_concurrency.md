---
title: "no concurrency"
date: 2009-05-31
forum: Hardware
---

### Post by cookie2009 on 2009-05-31
Hi,
I have the question about writing multi-thread programs on Ubuntu.
the problem is following:
I have a computer with intel pentium dual core (cpu info in attachmnt) and I would like to write two thread applicaction to test how it parrarel.
I was suprised the result, because when I use 1 or 2 procs  I can't see the program going faster 
1.86 on 1 proc and 1.72 on 2 procs on generic kernel and 
1.86 on 1 proc and 1.70 on 2 procs on server kernel.
I was a little bit confused because I had thought that this program is very good to parrarel,
so I decided to check it on server I have access to.
Ther result was different:
1 proc - 2.11
2 procs - 1.38
3 procs - 0.70
4 procs - 0.60
...
I include program I test and the results.
Might anyone tell me what could cause this situation.

I don't know what information are important to fing solution most of them are in listing.
One more: during the test I had enough memory all the time on both machines.

---

### Post by lisati on 2009-05-31
This might be better in the "Programming talk" subforum

---

### Post by cookie2009 on 2009-05-31
Ok, but how to change the subforum. 

As I wrote on server the program is ok so I'm thinking it's something wrong with my configuration and I put it here.

---

