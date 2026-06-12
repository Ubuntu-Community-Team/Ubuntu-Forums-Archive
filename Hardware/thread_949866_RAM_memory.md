---
title: "RAM memory"
date: 2008-10-16
forum: Hardware
---

### Post by tashe on 2008-10-16
I've been thinking lately about upgrading my RAM memory. Currently I've 2x256 MB DDR at 133mhz, with 2.93 Ghz Celeron, GeForce FX5200. I don't play much games so a good video card is not a necessity for me.
I's thinking buying 2x1GB DDR2 667mhz RAM, but I'm not sure if that will help cause my processor is not a very good one.
What do you think, is it good to do this or will it be more logical to buy 2x512 DDR2 RAM?
thanks

---

### Post by az on 2008-10-16
> **tashe said:**
> I've been thinking lately about upgrading my RAM memory. Currently I've 2x256 MB DDR at 133mhz, with 2.93 Ghz Celeron, GeForce FX5200. I don't play much games so a good video card is not a necessity for me.
I's thinking buying 2x1GB DDR2 667mhz RAM, but I'm not sure if that will help cause my processor is not a very good one.
What do you think, is it good to do this or will it be more logical to buy 2x512 DDR2 RAM?
thanks

Your processor is fine.  You will notice a performance improvement by increasing your ram from 512Mb.  If you can afford 2 Gigs, go for it.  

There is a bigger performance gain when going from 512 to 1 gig than going from 1 gig to 2 Gigs.  Depending on what you do with your computer, you may not appreciate the extra gig.  But it certainly won't do any harm.

---

### Post by kerry_s on 2008-10-16
you can't just buy any ram and stick it in.
what does your board support?
if it has 133mhz and that's what your board runs at, any ram you stick in there will run at 133mhz, if it works at all. you also want to check the max supported ram, for example this old laptop i'm using only goes up to 256mb ram maxed.

---

### Post by tashe on 2008-10-16
i took care about that.
My ASRock supports max 2gb ram at 667mhz

---

### Post by OrangeCrate on 2008-10-16
I'd add the RAM too.

I'm not sure you're suppose to do this on the forums or not, but this is a great place to buy RAM. I use them often when I'm cleaning up old computers. Friendly staff, good prices, and prompt service. I'm sure there are many other great sources too.

You can search for the exact RAM you need...

[http://www.memorygiant.com/](http://www.memorygiant.com/)

Edit:

Oops, I just noticed that you're in Europe. If they don't ship overseas, you can at least check the exact RAM you need on their site.

---

### Post by kerry_s on 2008-10-16
> **tashe said:**
> i took care about that.
My ASRock supports max 2gb ram at 667mhz

than by all means more is better. :)

---

### Post by Yellow Pasque on 2008-10-16
Wait a minute. You can't use DDR2 RAM in DDR slots. You need DDR sticks

---

### Post by Flag on 2008-10-17
I do appreciate all above, but having said this...why would you bother. Am using 2 gig of ram on an Acer 7520 dual processor, switched off the swap, and all it ever uses is something like 700 mb max, according the system monitor. So 1 gig should be fine, I think.
Software I run : Office, Firefox, Evolution, Skype, Photoshop CS 2 and under VMware XP with CS 3.

---

### Post by tashe on 2008-10-17
my board is some kind of transitional and it has w slots for DDR and 2 for DDR2, and also AGP, PCI and PCI express slots. A little from everything. :)
Thanks for the answers to all. I'm going to go with 2x1GB since the difference in price from 2x512 is less than 10 euro.

---

### Post by swoody on 2008-10-17
Good choice! I upgraded to 2gb as well, and even though I only have a 1.73ghz processor I noticed quite a difference in performance :D

I don't know if you knew, but the differences in mhz on RAM doesn't make a HUGE difference, so if there's some sticks at a lower mhz rating, for a lot less money, I would take that. Just my opinion :)

---

### Post by tashe on 2008-10-17
I did the upgrade few hours ago, bought 2x1GB DDR2 at 800Mhz, and even though my mobo supports 667Mhz it runs OK. I dont think that any problem will arise.

---

### Post by tashe on 2008-10-19
Now when I have upgraded the RAM to 2GB, is it possible to reduce the usage of virtual memory and make the PC use more of the RAM and less virtual memory? I think that way it will be better.
greeetings

---

### Post by Yellow Pasque on 2008-10-19
I think you're a bit confused on how a virtual memory system works. Linux is very good at managing virtual memory (unlike some other OS's that shall remain nameless), so users don't usually need to change any settings regarding virtual memory, especially if they have more than enough RAM for their usage.

If you want to read the technical details of tuning Linux's swapping policy, see: [http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

To see if any of your virtual memory pages are being swapped out to disk:
```
free -m
```

---

