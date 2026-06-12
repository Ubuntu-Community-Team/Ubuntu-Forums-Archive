---
title: "[SOLVED] Swap memory"
date: 2008-11-22
forum: General Help
---

### Post by DeMus on 2008-11-22
Hi,

Is there a reason why my computer, running Hardy 8.04, is using swap memory when there is still plenty of normal memory left?
I have 4 GB memory, running the 64 bits version, and am using 22% of the main memory. Still also some swap memory is used.
Any ideas?

DeMus

---

### Post by willypermana on 2008-11-22
You might want to edit the sysctl.conf file.
Quoted from [Jayson Rowe's blog]("http://jaysonrowe.wordpress.com/2008/10/05/ubuntu-tweak-guide/")
> Configure Swappiness:

Again, alt+F2, but this time enter:
```
gksudo gedit /etc/sysctl.conf
```
Add the line
```
vm.swappiness=n
```
To the end of the file where n equals a number between 0 and 100.

The default is 60

More than 1GB Ram, I reccomend 10
More than 2GB I reccomend 0
Less than 1GB, leave it alone!

Basically, with a setting of 100, the system will actively seek out stuff to swap, with a setting of 0 the system will rarely use swap (if at all).
On a side note, 4 GB ? To think that I only have 512MB RAM.....

---

### Post by DeMus on 2008-11-23
> **willypermana said:**
> You might want to edit the sysctl.conf file.
Quoted from [Jayson Rowe's blog]("http://jaysonrowe.wordpress.com/2008/10/05/ubuntu-tweak-guide/")

On a side note, 4 GB ? To think that I only have 512MB RAM.....

Thanks, this helped. Now the swap memory is reduced to 0.

---

### Post by benny bronx on 2008-11-23
I've previously read about reducing the swappiness, and finally took the plunge and set it to 0.  My system (1gb memory) seems more responsive, but this may be the freshly washed car syndrome. I'm just wondering if, when set to 0 or some other low value, would there be a noticeable slowdown when the swap partition must be used. In other words, does a low value cause a less seamless transition from memory to swap?

---

### Post by jimmy the saint on 2008-11-23
I wonder if that would impact hibernate.  The only reason I even have a large swap is so that hibernate will work (if, of course, it would actually work).

---

### Post by philinux on 2008-11-23
> **DeMus said:**
> Thanks, this helped. Now the swap memory is reduced to 0.

I'd be more bothered by the maxing out cpu's. Were you running something intensive at the time.

---

### Post by psychomichael on 2008-11-25
> **willypermana said:**
> 
On a side note, 4 GB ? To think that I only have 512MB RAM.....

hehehe...you make me feel positively rich with my current 6GB system...

---

### Post by fragos on 2008-11-25
I've 1GB and set my swappiness=10. I vertually never use swap space now and hiberante works properly -- to hibernate you need swap space => memory size.

---

