---
title: "[SOLVED] Out of disk space on / ?"
date: 2008-08-11
forum: General Help
---

### Post by Gatesgamer33 on 2008-08-11
Hi, I am getting errors when I try to update, that say that I am out of disk space. I go and look to see whats going on, and I discover that / is full. However, I cannot find what is willing up space through the Disk usage analyzer ](*,). Can someone please help me?

---

### Post by Gatesgamer33 on 2008-08-11
Bump.

---

### Post by damoxc on 2008-08-11
Do you have a separate /home to your /?

If not that could well be the problem there. Else I would check /var for disk usage as that is quite offending an offender of using up disk space.

---

### Post by hyper_ch on 2008-08-11
```

cd /
sudo du -R > /home/USER/Desktop/diskusage.txt

```

of coure you could first alter the df command to only go 1-2 levels deep and see what uses diskspace and then dig deeper from the according location.

---

### Post by damoxc on 2008-08-11
I'm guessing you meant:
```
du -h /
```

df show's how much diskspace an entire drive has used.

One of the first things you could run would be
```
sudo apt-get clean
``` which cleans out all the downloaded packages that apt has saved.

---

### Post by Gatesgamer33 on 2008-08-11
Thanks for the quick reply.:)

I have 5 partitions:

**Partition**     **Total**     **Free**     **Used percent**     **Filesystem Type**

**/**            18.6 GB    12 MB    99%              JFS

**/boot**        101.9 MB   51.9 MB  49%              Reiserfs

**/home**        210.9 GB   188.1 GB 10%              JFS

**/tmp**         894.2 MB   548.9 MB 38%              Reiserfs

**/var**         2.3 GB     1.3 GB   43%              Reiserfs

I don't have a swap partition, because I have 2 GB of Ram that never gets full :guitar:

Anyone know whats going on?

---

### Post by hyper_ch on 2008-08-11
yeah, I meant "du" ;)

---

### Post by Gatesgamer33 on 2008-08-11
Ok, heres the file with files in home directory left out (Gotta hide the personal info:))

Also I didn't want to clutter the thread with a 1000+ list.

---

### Post by sisco311 on 2008-08-11
[B]16G    /root/.local/share/Trash/files
7.9G    /root/.local/share/Trash/files/disk.2

[/B]Check root's Trash folder.

---

### Post by c2olen on 2008-08-11
As I see it, you might wanna clean up /root/.local/share/Trash
An example is "7.0G    /root/.local/share/Trash/files/2008-07-29_06.39.58.733637.mom-dad-pc.ful" as it eats up most of this filesystems space.

---

### Post by c2olen on 2008-08-11
> **sisco311 said:**
> [B]16G    /root/.local/share/Trash/files

[/B]Check root's Trash folder.


Sorry to have seemed to copy your post. I was typing it while you posted it in the mean time.

---

### Post by Gatesgamer33 on 2008-08-11
OMG! Thank you ALL SO much! You sirs, have just now earned cookies!

---

