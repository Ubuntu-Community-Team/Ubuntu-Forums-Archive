---
title: "need guidence in partition"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by rudi009 on 2009-02-06
this is what my hard drive looks like..
160gb total
(all partitions are NTFS formatted)
20gb windows installation
60gb other stuff
20gb free space$(the one i want to install ubuntu in)
50gb other stuff

i'm a newbie and i want to install ubuntu in that 20gb partition i mentioned with swap and everything(am i going right?).i'm using a live cd(8.10).

what i want to ask is do i need to format that partition before running the installation to ext3 or whatever(if yes then how?)?
second problem is that somtimes the installation starts and somtimes when i click on install it says that unable to load the 
xauthorization file.

please tell me everything in simple words.
help fast....

---

### Post by Niniel on 2009-02-06
Regarding your first question, yes, the partition should be formatted with ext3, but that can and will be done during installation.
If you want to, you can delete the 20 GB partition from within Windows (admin tools, computer management, storage/disks) and then just install to the free space, that might make it a bit easier to find. But it won't be a problem to do this with the partitioner that's part of the installation. 
For maximum control, partition manually (you'll need 2 partitions at least - / and swap; swap can be 0.5 - 2 GB depending your RAM and what you want to use the machine for; I have 1 GB of RAM/3 GB of swap space on one box, and 512 MB of RAM/512 MB Swap space on another. But according to the Gnome swap space monitor, it is very rare that any of that space is used at all, so I really don't think you need all that much). 
Sorry I can't help you with your second question.

---

### Post by rudi009 on 2009-02-06
i tried to install again and the install is not running.error is coming up and it says that unable to copy user's xauthorization file.not even the partition manager is running

---

### Post by Niniel on 2009-02-06
Could be that your installation CD has errors, unfortunately, that's not all that uncommon. 
Test the CD for errors (it's in the CD's boot menu).

---

### Post by spazz135 on 2009-02-06
Well I like your idea niniel but sometimes to many partitons can lead to problems. to me i would try another disk of ubuntu nad then make sure it is 8.10 preferably. And if there is any way just for you to put other stuff in one partition just to that and have like 3 or 4 only.:p

---

### Post by Niniel on 2009-02-06
No, that shouldn't be any problem at all. 
He has a total of 4 partitions, so they can all be primary partitions. He wants to dedicate one partition to Ubuntu - I don't see how that should not work. 
Regardless, the partitioner should always run. If it doesn't, to me, that suggests there's something else wrong.

So if it's not the CD, it could be that Windows wasn't shut down properly and that the NTFS disks are flagged as "dirty", in which case Ubuntu won't mount them. Doing a proper shutdown should solve that problem, but maybe it would be best to first delete from within Windows that 20 GB partition that is to be used for Ubuntu.

---

