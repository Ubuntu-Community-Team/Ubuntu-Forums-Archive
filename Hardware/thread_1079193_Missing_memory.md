---
title: "Missing memory?"
date: 2009-02-24
forum: Hardware
---

### Post by DPic on 2009-02-24
Ubuntu shows more RAM used in the resources tab than the total memory consumed by all the processes listed in system monitor. Why is this? Is this a bug? 

Thanks!
.danny

---

### Post by DPic on 2009-02-25
any ideas? does this happen to anyone else?

---

### Post by cariboo on 2009-02-25
The system monitor has some overhead of its own. On my computer, system monitor show about 640Mb usage, while free -m shows 619Mb used.

Jim

---

### Post by DPic on 2009-05-01
No, right now if i add up the memory being used by all the programs listed in gnome system monitor i should have less than 200MiB of memory used, but in the resources tab i have over 650MiB of RAM used and over 550MiB of swap space used. Should i file a bug report?

---

### Post by bubba_169 on 2009-05-01
> **DPic said:**
> No, right now if i add up the memory being used by all the programs listed in gnome system monitor i should have less than 200MiB of memory used, but in the resources tab i have over 650MiB of RAM used and over 550MiB of swap space used. Should i file a bug report?

Perhaps its used by daemons or other background processes? Otherwise it might be a memory leak? Does the used memory increase the longer you use your computer?

---

### Post by DPic on 2009-05-01
> **bubba_169 said:**
> Perhaps its used by daemons or other background processes? Otherwise it might be a memory leak? Does the used memory increase the longer you use your computer?

It seems to, very slowly, if at all, so i'm not sure. As soon as i start up my machine my memory consumption already looks pretty much like this. Shouldn't the system monitor list daemons and background processes?

---

### Post by blackened on 2009-05-01
> **DPic said:**
> No, right now if i add up the memory being used by all the programs listed in gnome system monitor i should have less than 200MiB of memory used, but in the resources tab i have over 650MiB of RAM used and over 550MiB of swap space used. Should i file a bug report?

What does free -m show in comparison? 

Is the system really using that much memory, other than caching and buffering normally, or is System Monitor misreporting usage?

---

### Post by DPic on 2009-05-01
> **blackened said:**
> What does free -m show in comparison? 

Is the system really using that much memory, other than caching and buffering normally, or is System Monitor misreporting usage?

~$ free -m
             total       used       free     shared    buffers     cached
Mem:           987        967         20          0         23        165
-/+ buffers/cache:        778        209
Swap:         1302        593        708

---

### Post by DPic on 2009-05-01
> **DPic said:**
> It seems to, very slowly, if at all, so i'm not sure. As soon as i start up my machine my memory consumption already looks pretty much like this. Shouldn't the system monitor list daemons and background processes?

I take back what i said earlier, my computer doesn't start up with this much memory used up, but still significantly more that should be used. I ask again, shouldn't the system monitor list daemons and background processes?

---

### Post by DPic on 2009-05-02
Sorry to triple post, but i wanted to bump this and add more info. It seems to affect all programs. Everything uses more memory than system monitor indicates. When i end any process, a lot more memory is freed than system monitor says it used.

---

### Post by DPic on 2009-05-02
I've filed a bug report... [https://bugs.launchpad.net/ubuntu/+bug/370998](https://bugs.launchpad.net/ubuntu/+bug/370998)

---

