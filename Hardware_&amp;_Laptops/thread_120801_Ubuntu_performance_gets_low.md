---
title: "Ubuntu performance gets low"
date: 2006-01-23
forum: Hardware &amp; Laptops
---

### Post by newuser111 on 2006-01-23
with 256 of ram you should have created a swap partition, only with 1gb+ can you get away without a swap.  

you can create a swap file instead of a swap partition read [http://enterprise.linux.com/article.pl?sid=05/03/02/2250257](http://enterprise.linux.com/article.pl?sid=05/03/02/2250257)

---

### Post by barisurum on 2006-01-23
Hi there
 
   I have used Ubuntu for a short while, I was using Fedora 3 before. I have the same problem I got there. The system boots well and works nice for a while and after some
apps or 2-3 apps working together the system gets too slow and I think it flushes the memory to harddrive. So I have to reset the computer!

   I didnt create a swap in install. Is it because of that?
   
   My memory is 256 MB

   When I run "free" it shows:
                              total       used       free     shared    buffers     cached
Mem:        224480     219952       [COLOR="Red"]4528[/COLOR]          0      10664      98256
-/+ buffers/cache:     111032     113448
Swap:            0          0          0

   Can I create a swap without deleting files now? or is it possible to make Ubuntu work better without it?

  Thanx

---

### Post by barisurum on 2006-01-24
OK. I created a "file swap" with your help. But it says making a swap partition while install is better than this. Is it so important?
   I made a 512 MB swapfile.
   Thanks

---

