---
title: "Missing hard drive space"
date: 2008-09-16
forum: General Help
---

### Post by Nisuspi on 2008-09-16
Hi all,

I'm hoping someone can help me - I'm new to Linux and I'm curious to know where my hard drive space has gone. 

Every time I delete a file it vanishes from the system, but the overall space available doesn't go back up.

For example - I've been playing around with VMWare server to see if I can get some business critical Windows programs running. I set up a 25GB virtual machine, when I deleted it I never got the 25GB back.

According to Nautilus and the Disk Usage Analyser, there are around 60GB of files on my 750GB hard drive - which sounds about right. According to the totals in top line analysis of both, there's 140GB of space used. 

I've emptied the trash, cleaned up the hidden files and wiped the apt download cache. Is this a common bug and my Google-fu has failed me, or am I missing something?

---

### Post by Infinite Indefinite on 2008-09-16
Check /var/backup/

sudo du -h /var/backup

(For further details:

[http://ubuntu.philipcasey.com/04/10/2007/low-disk-space/](http://ubuntu.philipcasey.com/04/10/2007/low-disk-space/) )

---

### Post by cariboo on 2008-09-16
The graphical Disk usage Analyzer doesn't report the actuall used space as it also includes gvfs usage, which effectively doubles the used hard drive space. to get a true reading in a terminal type:

```
df -h
```

This will give you a better reading of how much of your hard drive is being used.

Jim

---

### Post by niteshifter on 2008-09-16
> **cariboo907 said:**
> The graphical Disk usage Analyzer doesn't report the actuall used space as it also includes gvfs usage, which effectively doubles the used hard drive space. to get a true reading in a terminal type:


It does?

```
dlk@dlk-lt-1420:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             101G   52G   45G  54% /
varrun               1013M  112K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   84K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   34M  980M   4% /lib/modules/2.6.22-15-generic/volatile
dlk@dlk-lt-1420:~$ 

```

---

### Post by bingoUV on 2008-09-16
Run the graphical disk usage analyzer as root. I think the command is baobab:
```

sudo baobab

```

---

### Post by Nisuspi on 2008-09-16
Brilliant - thanks for the help and quick replies guys.

The back-up library showed as non-existent, curiously, which makes me think I've managed to bork something important.

'-df h' showed the same as Disk Analyser - total space 682G, used 72G, free 577G, same cooky maths, and sure enough gvfs shows up with an entry exactly the same size as my file system.

Running boabob as root does show what I expect - 682G total, 610G free.

I'm a little hazy as to the inner workings of gvfs - does it start afresh every time you boot? What happens when you reach 50% disk usage?

---

