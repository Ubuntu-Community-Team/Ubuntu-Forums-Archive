---
title: "where'd all my space go :("
date: 2008-07-14
forum: General Help
---

### Post by Existance0 on 2008-07-14
I made a 40 gig partition for Linux installed it at 10 gigs and didn't really install much if I right click on my filesystem and go to properties it says 12 gigs used but at the bottom of the window it says 4 gigs free? Somethings not right there.

---

### Post by fyo on 2008-07-14
Could you open up a terminal and run "df -h"?

To see where your disk space got to, you can try "du". It's quite a useful little tool that'll give you the disk space used for a particular folder (usage e.g. du -h --max-depth=0 /var/ )

---

### Post by Existance0 on 2008-07-14
```
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      8.4G  3.9G  4.1G  49% /
varrun                251M  112K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M   56K  251M   1% /dev
devshm                251M   12K  251M   1% /dev/shm
lrm                   251M   39M  213M  16% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      8.4G  3.9G  4.1G  49% /home/arie/.gvfs
/dev/scd0             2.6G  2.6G     0 100% /media/cdrom0

```

I think I know what the problem is but I don't know how to fix it when I installed Ubuntu it asked me for an installation size and I put 10 gigs which is what is now being used but when I put that I wasn't sure what it was talking about. So is there a way to change that without reinstalling Ubuntu?

---

### Post by forger on 2008-07-14
Applications > Accessories > Disk usage analyzer > Scan filesystem :)
shows you in detail which files/folders use up most of your space

---

### Post by Existance0 on 2008-07-14
[img]http://img504.imageshack.us/img504/514/screenshotdm9.png[/img]

---

### Post by fyo on 2008-07-14
Next step is to run GParted. If your file system isn't as big as your partition, or if your partition doesn't take up all the space, there's an easy solution (resize2fs for the former, GParted for the latter).

---

### Post by Existance0 on 2008-07-14
I'm not sure what that last part you said was but heres the picture and it does say I have 30 gigs unused.
[img]http://arch-games.com/Screenshot.png[/img]

---

### Post by Existance0 on 2008-07-14
Sorry for bumping so soon but I really need to get this fixed asap.

---

### Post by sayakb on 2008-07-14
What are the files in the /host folder?

---

### Post by fyo on 2008-07-14
Which one's the 40gig partition for Linux?

One of the NTFS volumes? That's just asking for trouble. NTFS is Microsoft's file system. It's supported under Linux and I've had no problems (reading or writing) with the new ntfs-3g stuff, but it's not exactly FAST. It seems to use a lots and lots of CPU.

For Linux, you really need to chose a different file system... like ext3 (Ubuntu default).

Honestly, if you went NTFS for your Linux file system, I think you're better off reformatting and reinstalling.

---

### Post by Existance0 on 2008-07-14
Hmm I really don't want to do that but what I will do is take that extra 30 gigs make it a new partition transpher the files there and then re add the extra space to it :D don't lose data then.

---

### Post by sea_monkey987 on 2008-07-14
is this a wubi install?  judging from your df -h and gparted screenshot, I'd guess that it is because it makes no sense why your ubuntu is on a 8.4GB partition and the gparted screenshot shows a 40GB partition as your mounted one along with the fact that you don't have a 8.4GB partition on your actual hard drive.

---

### Post by fyo on 2008-07-14
I have resized NTFS partitions with GParted without problems, so you probably could go that route.

Remember that you can only resize partitions that aren't mounted, so you're going to need a boot disk (or cd or dvd) with GParted.

---

### Post by avtolle on 2008-07-14
That most definitely looks like a wubi install. The OP needs to look at the Wubi Guide (sorry for no link) for information about resizing/adding a virtual disk.

---

### Post by Existance0 on 2008-07-15
Well I formated the ubuntu partition and now am reinstalling it but I don't want there to be any limit on the space it uses... And the max the windows installer allows is 30gigs can someone tell me how to not make a limit.

---

### Post by Elfy on 2008-07-15
If you're trying to put it in the same place - then there is only 30 Gb free.

If you want to use the whole partition why don't you make it a dual boot instead of a wubi installation.

You might also find more info in that forum- not sure though.

I found the guide

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

