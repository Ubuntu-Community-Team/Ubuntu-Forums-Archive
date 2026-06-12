---
title: "Home folder appears full"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by gallaharsha on 2009-06-23
Hi,

I m using Ubuntu Jaunty and I have allocated around 5 Gb to Home and 20 gb to root partitions.I don't understand that within few days of use I am not able to perform anything like writing a text file. It shows me an error that there is no space on home. How to overcome this error.

Best Regards,
Harsha galla

---

### Post by raymondh on 2009-06-23
> **gallaharsha said:**
> Hi,

I m using Ubuntu Jaunty and I have allocated around 5 Gb to Home and 20 gb to root partitions.I don't understand that within few days of use I am not able to perform anything like writing a text file. It shows me an error that there is no space on home. How to overcome this error.

Best Regards,
Harsha galla

 /home is for your personal files and settings ..... have you been putting such in your system?  

In terminal, type and post back results of

```
df -h
```

A link for reading.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by gallaharsha on 2009-06-23
This is what i get with the above command:

> ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              19G  3.2G   15G  18% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  212K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  172K  249M   1% /dev
tmpfs                 249M  112K  249M   1% /dev/shm
lrm                   249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb3             4.6G  4.4G   25M 100% /home
/dev/sdb6              26G   22G  4.2G  84% /media/sdb6
/dev/sda5              30G   14G   16G  47% /media/sda5
/dev/sda6              21G   16G  5.7G  74% /media/sda6
/dev/sdb5              25G   15G   11G  59% /media/sdb5
/dev/sda1              25G   19G  5.8G  77% /media/Windows
```

---

### Post by merlinus on 2009-06-23
From what I can see, you have two choices:  move some of your data from /home to a different partition, or use gparted to shrink sdb5 and add the freed-up space to it.

Obviously a third is to archive material from /home to dvds or external drive.

Although this is the proverbial locking of the barn door after the horses have fled, whenever installing a new os it is well worth the time to do some investigating beforehand, as well as assessing your specific needs.  For example, 7G for / is more than enough, and then you would have had lots more space for /home.

---

### Post by gallaharsha on 2009-06-23
Hi, 
I already have windows xp and windows 7 partitions among those while the sdb5 u have suggested to shrink is a junk. Will i have any issues accessing this partition from windows??
Thanks for your reply

---

### Post by merlinus on 2009-06-23
Only if formatted as ntfs, and although linux can read and write to it, you cannot use it for /home.  You can, however, install Ext2 IFS which will allow windows to read and write to ext2 and ext3 partiitions.

BTW, although a bit tricky since it seems as though you have an extended partition on sdb, you might be able to shrink / and add the space to /home.

---

### Post by gallaharsha on 2009-06-23
The sdb5 is on the other hard disk so how to I change the mount point to /home which is on the other hard disk..??

---

