---
title: "RAM vs Cache"
date: 2018-05-18
forum: Hardware
---

### Post by imgeka on 2018-05-18
I have Ubuntu running on a 3 GB RAM machine; things do slow down at times. According to the System Load Indicator, the machine is occasionally utilising 2,2 GB RAM **plus **1,4 GB cache, i.e., a total of 3,6 GB on a machine with 3 GB installed RAM.

My question is perfectly straightforward: Is the utilised cache part of the 3 GB RAM that I have installed on my laptop?

I have googled this question, but I have not come across a single straight answer.

Thanks in advance.

---

### Post by cruzer001 on 2018-05-18
Hello

For starters, have you seen this?
[https://www.linuxatemyram.com/](https://www.linuxatemyram.com/)

3G of ram should get you by for everyday use.  If your going to swap before using all your ram, then "swap" needs to be tweaked.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by imgeka on 2018-05-18
Hi,

It's still a bit confusing.

An unequivocal answer to this question would be really helpful: Is the utilised cache part of the 3 GB RAM that I have installed on my laptop?

---

### Post by cruzer001 on 2018-05-18
Any extra ram can/will be used by cache, but the system can take it away from cache when ever system requires it.  So yes to your question.

---

### Post by imgeka on 2018-05-18
Stupid question perhaps: if I upgrade from 3 to 4 GB RAM, will it make my laptop somewhat faster?

---

### Post by cruzer001 on 2018-05-18
Nope

Unless you are using swap at times of heavy use.  I have installs running dual core and 3G of ram, works for me.

Please post your memory usage.
```
free -m
```

---

### Post by cruzer001 on 2018-05-18
You can notice a difference in speed when using the ubuntu flavors.

I also run Mate and its noticeable faster than Ubuntu even on my quad core.

---

### Post by imgeka on 2018-05-18
total        used        free      shared  buff/cache   available
Mem:           2993        2311          80         374         601         112
Swap:          2037         132        1905

Screenshot here:

[https://imgur.com/a/PatctIO](https://imgur.com/a/PatctIO)


Looking at these figures, is a 1GB RAM upgrade feasible? Might it make a difference?

---

### Post by cruzer001 on 2018-05-19
Looks like you have used a little swap space, an extra gig would be fine, just not any faster other than keeping you out of swap usage which is slow.  Your cache is using  about  gig which is what I typically run.  I run virtual systems and have varied the amount of ram up to 6G and found 3G of ram sufficient.

it gets used
```
              total        used        free      shared  buff/cache   available
Mem:          11964        7483        1936         260        2545        4804
Swap:          2047           0        2047
```

---

### Post by Autodave on 2018-05-19
Adding one gig of ram is not going to make a noticeable difference.  

The first thing that I would do is choose a lighter desktop: Ubuntu is rather heavy.  As cruzer001 already suggested, Ubuntu Mate or (my favorite) Xubuntu would be a better choice for that machine. And, it won't cost you anything. :-)

As far as adding more RAM you would have to see what is in there. Your 3 gig could be one piece or 2 pieces of memory. If it is one piece, then you could easily install a second piece of 3 gig as long as it matches the first one. Some computers do not mind there being 2 different sizes of memory sticks, some will not work at all with it mismatched.

---

### Post by imgeka on 2018-05-19
OK, thanks to both of you for your input.

My laptop has two RAM slots and it is running fine with 1+2 RAM from two different manufacturers.

I will try out Xubuntu; I have read that the Ubuntu Mate is no longer the lightweight distro it used to be.

---

### Post by Autodave on 2018-05-19
I was running Xubuntu 16.04 on an old ASUS-EEEPC: 1 gig ram, 700mhz single core. And it ran surprisingly well: was quite usable and very stable.

---

### Post by cruzer001 on 2018-05-19
> **imgeka said:**
> I have read that the Ubuntu Mate is no longer the lightweight distro it used to be.

Don't believe everything you read :)

Burn some DVDs of the different flavors and try them out without installing.  The best test is your test.

---

