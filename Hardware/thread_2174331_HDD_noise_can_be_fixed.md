---
title: "HDD noise can be fixed?"
date: 2013-09-13
forum: Hardware
---

### Post by jeehyun on 2013-09-13
Now I have ubuntu on lenovo latop.
SSD has no noise. But storage size is small.

I want to install ubuntu on hdd but I have experienced agressive noise on hdd before.

I have tried several solutions advised but can not fix this problem.
For example, sudo hdparm -B 255 /dev/sda, sudo hdparm -B 254 /dev/sda or sudo touch /etc/pm/power.d/95hdparm-apm

Is there anyone that knows answer for this?
or it's normal? So SSD is only solution?
Thanks.

---

### Post by carl4926 on 2013-09-13
Buy quality HDD
Use a quality case with soft mounts

---

### Post by jeehyun on 2013-09-13
Sorry I mean laptop hdd.

---

### Post by carl4926 on 2013-09-13
Sigh....
Quality HDD

Has it been possible for you to ascertain the source of the noise: ie; is it the HDD generally or is it seating badly and creating noise from contact with surroundings. If the latter you could look at adding a buffer, sometimes 'Carefully' placed sticky fixers will do...

---

### Post by jeehyun on 2013-09-14
I don't know what is quality hdd, what is contact with surroundinds, what is buffer. ok?
Very strange electric sound.
On windows no problem.

---

### Post by jeehyun on 2013-09-14
I copied other post from linuxforums.org
It seems same thing.

 **Hard drive makes funny noise in Linux, but not in Windows...**

[INDENT]                             I recently installed Mint Linux on my desktop. Weird thing...  whenever I'm in Linux, my hard drive makes a funny noise when accessing,  I can hear all the activity when it's accessing. If I reboot into  Windows, it doesn't make the noise, only when I'm in Linux.
 
What could cause that? Does Linux have some different way of accessing  the hard drive that would make it make noise? I'm worried that it's bad  for my hdd too. Any ideas?                         
[/INDENT]

---

### Post by carl4926 on 2013-09-14
OK, so now we are getting somewhere.

So you HDD makes lots more noise in Linux than in Windows.
I never experienced this myself. And it does sound like it's not an environmental issue or even a hardware quality issue. Rather, some as yet, unknown ?

One thing that Linux does do is indexing and I have found some noise during this process, but nothing excessive.

---

### Post by jeehyun on 2013-09-16
I found this is just hdd vendor's problem.
I changed oher vendor's hdd and no electric noise.
I can not say what company it is.:cool::cool:
Because this problem may be also connected with certain motherboard.
Anyway I am happy.

---

