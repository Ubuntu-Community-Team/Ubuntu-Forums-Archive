---
title: "[SOLVED] incorrect reading of disk space"
date: 2008-07-22
forum: General Help
---

### Post by Riffer on 2008-07-22
I have a 60 gig HD that I partitioned into 3 sections of equal size.  One I use for Ubuntu, one for VMWare and the last as storage.

Right now my Ubuntu partition says I have 968 megs of space left, yet I know I've only use a small portion of it.  Any ideas why?

---

### Post by hyper_ch on 2008-07-22
I guess because you filled the partition up to that on 1 gb that you didn't fill yet.

---

### Post by Riffer on 2008-07-22
Ok I'm probably not very clear.  The Ubuntu partition is about 18 gigs of space.  I've used maybe 7 gigs of it, yet in "system monitor" it says I've used 17 gigs.

I'm worried that my affect my performance etc.

---

### Post by hyper_ch on 2008-07-22
well, I still think you have used 17 gigs... otherwise it would not show 1 gb free

---

### Post by Riffer on 2008-07-22
Well if I do a "properties" on my root folder, I show 4.9 gigs.

---

### Post by hyper_ch on 2008-07-22
```

df -l

```

```

sudo fdisk -l

```

---

### Post by Riffer on 2008-07-22
I have 2 screenshots, one shows the output to the code you gave, the other shows the output for a utility "disk usage".

It seems to me that its reading the other partitions and including them into the Ubuntu partition size.  I don't have the other 2 automounted  so I wonder if thats what's going on?

---

### Post by Riffer on 2008-07-22
Automounted the other 2 partitions, still same problem.

---

### Post by plucky on 2008-07-22
According to the second screenshot,your / partition is 92% full so something is eating up your disk space.

Open a terminal and post output of ```
sudo fdisk -l
sudo find / -type f -size +100000k
```

The second command will search for large files on your linux partition,if it doesn't find anything,reduce it to 50000k and try again.

Have you got a simple backup process running in the background?
Check your /var/log files for a log file that is getting out of hand.
Clear out Trash and Root Trash.
Clear out downloaded .deb files.


Good Luck

---

### Post by Riffer on 2008-07-22
That's it, its all in the root trash.

How can I delete stuff in the root trash?  I tried 

"sudo nautilus"

but no go.:S

---

### Post by plucky on 2008-07-22
> **Riffer said:**
> That's it, its all in the root trash.

How can I delete stuff in the root trash?  I tried 

"sudo nautilus"

but no go.:S

Try ```
cd /root/.local/share/Trash/files
``` Then ```
ls -l
``` to list the files in that directory,
and to delete ```
sudo rm -rf *
```
[color=red]Only use the last command if you are sure you are in the correct directory[/color] as it is one of those dangerous commands.

Good Luck

---

### Post by Riffer on 2008-07-22
Fixed it.  I needed to use

"gksudo nautilus"

go into the root trash folder and use the "del-shift" combo to delete everything.

Marking this solved thanks for your help.

It does beg the question of why Ubuntu has this seperate folder for trash?  And is there an easier way to clear it out?

---

### Post by cariboo on 2008-07-22
Ubuntu has a seperate trash folder for each user, and root is a valid user. The only time trash goes to the root trash is when you delete files as root.

Jim

---

