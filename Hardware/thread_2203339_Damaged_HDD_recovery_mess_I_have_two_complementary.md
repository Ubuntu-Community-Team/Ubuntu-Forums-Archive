---
title: "Damaged HDD recovery mess: I have two complementary .dd files"
date: 2014-02-02
forum: Hardware
---

### Post by timonoj on 2014-02-02
Hi guys,

Maybe some of you can help me. I have a failed USB 320GB HDD from my gf, and of course she didn't have any additional backup of it. I unmounted the USB case and connected it through SATA.
It has three partitions. The last one is the biggest with 160GB, and the one that took the brunt of it. It's also the most important one to her. It's damaged around the 8GB point, so whenever the computer reaches that part, starts to slowly stall and in the end it hangs completely.  This crashes happens both from Hiren's MiniXP, a normal Win7 environment, Gparted and Ubuntu. Not that I didn't try!

I got recommended to do a backwards .dd backup. And it mostly worked, because it managed to pull 149GB backwards before it crashed. Then I have the initial forward .dd backup with the initial 8.49GB. So what I have is:

-Backup from start, 8.49GB.
-Backup starting from the end, 149GB. 
So the question is....Is there a way to piece them back together and attempt to recover the file structure? The partition is NTFS.

Thanks!

---

### Post by oldfred on 2014-02-03
Are you using gddrescue?

 gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
[http://wiki.linuxquestions.org/wiki/Dd_rescue](http://wiki.linuxquestions.org/wiki/Dd_rescue)
gddrescue better than ddrescue
[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

---

### Post by timonoj on 2014-02-03
Thanks oldfred!
I got the .dd files with DataRescueDD, running from a miniXP from Hirens BootCD. I attempted previously other solutions running on a couple PCs, such as norton for linux, for windows, teracopy and so on. In all cases the HDD reaches a point where it crashes the running OS.
I can try to tun gddrescue, but I believe it won't change the result, with the backup crashing exactly in the same place. I don't think I can run a full partition backup. I'm trying to move on from attempting further backup files, as I think this is as far as I'll get, this 149GB and the 8GB. Is there a way to get the data from these ones? If you think any other backup format will give me a better chance to get data from an incomplete backup, I can run that one, hoping that after crashing the resulting file can be read.

---

### Post by oldfred on 2014-02-03
I do not know how to combine them. 
That is an advantage of gddrescue that it tries several ways and then skips a defective sector. so the copy is everything but the defective sector, which of course could be a major issue.

Can you create a new partition of exactly the same size. Write the first 8.49 GB from front and write the rest from the back. I have never seen nor used reverse dd, so do not really know.

---

### Post by timonoj on 2014-02-05
Thanks for your help. I'm using gddrescue now, and I have to give it to you, this thing is way more stable than any other software I tried before. It keeps going through all the mess of damaged sectors (using the -n option first). So that's that. It's been a full day and it's still stuck at the first 9GB of data, but it really keeps going and changing of sectors after a while. At a crawl pace, but that's fine to me, I have a spare machine to use at the office.

---

