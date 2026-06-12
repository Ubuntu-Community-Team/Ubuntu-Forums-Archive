---
title: "[SOLVED] Hard drive?"
date: 2008-08-19
forum: General Help
---

### Post by Yezinki on 2008-08-19
Hi there,

What should be the partitioning strategy for a drive in 2 situations.

1.Installing Ubuntu alone.

2. Vista with Ubuntu.

Please take it easy on me & don't mind my questions I know am a bother but a newbie to this Ubuntu world.

Hoping to hear elaborately from you.......

Thanks in advance!

---

### Post by tamoneya on 2008-08-19
1.  2 GB swap partition
    10 GB root partition "/"
    rest for /home

2.  40 GB for vista
    2 GB swap partition
    10 GB root partition "/"
    rest for /home

---

### Post by tuxxy on 2008-08-19
Maybe you should read a guide on partitioning before you attempt it,

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by petedct on 2008-08-19
Here's a great [place]("http://www.psychocats.net/ubuntu/partitioning") to learn about partitioning. It speaks to XP but Vista shouldn't be much different.

---

### Post by Yezinki on 2008-08-19
> **tamoneya said:**
> 1.  2 GB swap partition
    10 GB root partition "/"
    rest for /home

2.  40 GB for vista
    2 GB swap partition
    10 GB root partition "/"
    rest for /home


Thanks .....what should be first.......swap, root, home?

symbols like /sd, /sd/dev, /sd/dev1/2/4/5/6/7 are confusing?

I appreciate your guidance!

---

### Post by Yezinki on 2008-08-19
Can any of you suggest how I could fix my present drive error issues?

Thanks for the great links!!

---

### Post by tuxxy on 2008-08-19
The guide is there, read the link! :)

---

### Post by tamoneya on 2008-08-19
> **Yezinki said:**
> Thanks .....what should be first.......swap, root, home?

symbols like /sd, /sd/dev, /sd/dev1/2/4/5/6/7 are confusing?

I appreciate your guidance!

since they are all on the same disk they would all start with /dev/sda.  As for the number following that it isnt all that important in what order they go but they would be something like this:
vista: /dev/sda1
swap: /dev/sda2
root: /dev/sda3
/home: /dev/sda4

---

### Post by Yezinki on 2008-08-19
This post:  Drive Partitioning Error?

---

### Post by Yezinki on 2008-08-19
I am getting errors when I try to install.

LowSky's comments are: 

```
Quote:
Originally Posted by Yezinki View Post
Hi,

Whats wrong with the drive partitions that KDE wont install??

Thanks!
Your / and /home... are both the same size. which is impossible I would fix that. By the way / only need to be about 15GB, you can give the rest to /home
```


How do I fix this??

What should be the partitioning strategy for a SINGLE boot drive using Ubuntu & for a DUAL boot with Vista & Ubuntu??

Hoping to hear from you smart people,

Thanks in advance![/QUOTE]


> **Yezinki said:**
> How do I correct/fix this??

Thanks!

---

### Post by Yezinki on 2008-08-19
How do I do what lowSky suggests??

---

### Post by tamoneya on 2008-08-19
im really not following lowsky.  I cant really see what the problem is and what his solution is.  Also some of his statements dont make sense.  It is not impossible for / and /home to be the same size.

---

