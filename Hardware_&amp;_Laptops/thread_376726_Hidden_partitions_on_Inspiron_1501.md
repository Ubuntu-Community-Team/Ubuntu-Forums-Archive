---
title: "Hidden partitions on Inspiron 1501"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by dashnak on 2007-03-05
Hey:
I've recently bought a Dell Inspiron 1501....
While partitioning the HD I found 2 hidden partitions: One for the diagnostics program, and one is for recovery (3 WHOLE GB!!). My question is, can I erase the recovery partition? I mean, Dell sent some disks in my package and those say restore as well: also, I really don't think my edgy installation would come out unscathed of such "restoration", so it is useless to me, as I would have to do everything by hand... Am I right?
Thanks
dashnak

---

### Post by Zac Dai on 2007-03-05
I was just wondering myself as I have a Dell dimension 3000 with a blank 3gb partition and a dell utility partition. I want to get rid of them but I'm not sure if it would effect my dual boot with windows.

---

### Post by halw on 2007-03-05
If you are planning to dual boot, yes you had better keep your recovery partition. On the other hand, if you are blowing away windows, as I have done, just let Ubuntu take over the entire disk.

Edit: If you are planning on dual booting, make sure to defrag windows prior to installing Ubuntu.

---

### Post by dashnak on 2007-03-05
I'm dualbooting. What's the use of such recovery partition? I mean, if something in windows crashes, it will restore windows, killing ubuntu in the process, as it reformats everything. If something in ubuntu crashes, it won't be fixed, at all, by the recovery. So?

---

### Post by brettr on 2007-03-05
I am running an inspiron 6000, i hosed my recovery partition, and called dell and got them to ship me the proper cd's. I needed the extra 3 gb :). Although i am using linux completely now so i dont really need the cd's anymore.

---

### Post by dashnak on 2007-03-05
So in the end it doesn't really matter? I mean, those are 3 GB that could be put to very good use.... And windows is disposable anyway, if it breaks, I will have to fix it by hand, as doing it with the recovery would kill Edgy..

---

### Post by Ek0nomik on 2007-03-05
I dual boot.

As soon as I got my laptop (Inspiron E1505) I knocked out the Windows they gave me and created 1 single partition for Windows.  Than I created my EXT3, Swap, and FAT32.  I completely got rid of the recovery and media direct partitions.  If Windows breaks, reformatting always works better in my opinion.

---

### Post by dashnak on 2007-03-06
Hell yeah... That recovery partition is going down....

---

### Post by SnowPunk98 on 2007-03-06
Feel free to get rid of the partitions, you don't need them. I have an E1705 and got rid of both of mine, however be aware that the MediaDirect partition hides in the HPA. When I first setup my machine I got everything setup the way I wanted and then accidentally pushed the MediaDirect button when the machine was off and it screwed up my Windows partition. 

This should only apply if you are using version 1 or 2, version 3 is a regular partition.

---

### Post by dashnak on 2007-03-06
Doesn't matter... the 1501 doesn't come with mediadirect, or media keys for that matter, so I'm all set....
Thanks

---

### Post by dashnak on 2007-03-08
Ok, time for the "I-told-you-so"s... I did delete the partition, enlarged the logical partition which contained my root filesystem and swap, and added that empty space to my root....
Everything worked fine, or so I thought....
Now, some Live CDs simply won't boot, or will crash as soon as I do something... An example is geexbox, it freezes when it finds my hd and tries to mount it......
Does anyone have any ideas? I'm starting to think that I'll have to wipe EVERYTHING and start all over again...

---

### Post by dashnak on 2007-03-08
Something? Anyone?

---

