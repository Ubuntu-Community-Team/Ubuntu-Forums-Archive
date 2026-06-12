---
title: "Can't remove a partition.. dismount all logical partitions first??"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Meiji on 2009-05-18
Hello Everyone!

Well, following [this thread]("http://ubuntuforums.org/showthread.php?t=1161640"), I had a problem trying to make security upgrades to my Ubuntu, thus, it didn't even let me surf the Internet nor take screen caps. I then realized (thanks to **taurus**) it was because I only gave Ubuntu a small amount of disk space when I installed it.

Solution was deleting /dev/sdb6 so that space would become unallocated. Then expanding /dev/sdb7 to take up that new unallocated space. So, I made all necessary backups to /dev/sdb6, boot my PC and started with the Ubuntu LiveCD (where I am now), executed GParted and, after several hours lol, it finally show me the window where I can see all the partitions.

Now, everytime I try to delete /dev/sdb6, it shows me this warning message:

[B]Imposible erase /dev/sdb6.
Please, dismount all logical partitions with a number greater than 6[/B]

Thus, I'm stuck here and cannot remove /dev/sdb6. I'm kinda newbie with Ubuntu, so, anyone knows why is this happening and what I must do?

Thanks in advance!
Meiji

---

### Post by logos34 on 2009-05-18
it's probably activated your swap--does that automatically.  Right-click on swap>swapoff.  Now try delete again

---

### Post by Meiji on 2009-05-18
Thanks! But where can I find the swap option?? Sorry, I know it could sound stupid lol =P but that's because I started Ubuntu Live CD in Spanish and sometimes translation is lost when using technical words. =P

---

### Post by logos34 on 2009-05-18
sorry, I shoulf have said right-click **in Gparted** on the swap partition...

---

### Post by logos34 on 2009-05-18
making any progress? 

neither swap nor any partitions inside that extended partition (i.e. logical paritions numbered 5 or higher) can be mounted during the delete and resize operation

---

### Post by Meiji on 2009-05-18
No progress it seems... I right click on the swap partition and then select swapoff, but I now got this message:

[B]Swap area cannot be disabled

Killed[/B]


Is my Ubuntu dead? =( ...

---

### Post by Meiji on 2009-05-18
Question: Couldn't I just format that partition (dev/sdb6) and then try to assign that space to dev/sdb7 ??

---

### Post by Meiji on 2009-05-18
Well, I made an experiment, and it seems I succeeded!! I read the information of both dev/sdb6 and 7, and I realized they were no mounted; so, I resize dev/sdb6 and suppressed only 10mb of it. It created a new "without assing" slot, then I added those 10mb to dev/sdb7, and voilà! It worked! :D

The good: I'm happy now! lol
The bad: It took its time!!! They were only 10mb, and spent about half an hour T.T ...
The ugly: This will be a looong looong night T___T

Thank you very much for your help logos34!! You really helped me understand what was happening! Though I'll be back if I got any other problem =P

Cheers!
Meiji

---

### Post by Mark Phelps on 2009-05-18
In future, you will find it much easier to do partition work using the GParted LiveCD instead of booting from the Ubuntu CD, because the GParted LiveCD doesn't mount any of the partitions.  Also, it's a newer version than the one bundled with Ubuntu.  You can get it from the distrowatch.com website.

---

### Post by logos34 on 2009-05-18
> **Meiji said:**
> Well, I made an experiment, and it seems I succeeded!! I read the information of both dev/sdb6 and 7, and I realized they were no mounted; so, I resize dev/sdb6 and suppressed only 10mb of it. It created a new "without assing" slot, then I added those 10mb to dev/sdb7, and voilà! It worked! :D


sorry I couldn't hang around any longer early this morning, had to go...

anyway, glad you're making progress.  But to tell the truth I've never seen those exact Gparted error messages..."without assing" slot, huh?  Maybe something's changed in Jaunty (I'm still on 8.04 Hardy)...Why is it only letting you shrink the partition down incrementally?    

can you run this in a terminal and post:

sudo fdisk -l


btw, about this:

> Couldn't I just format that partition (dev/sdb6) and then try to assign that space to dev/sdb7 ??

can't do that, unfortunately...can't merge or join two separate partitions...you can only *expand* one partition into *unallocated space*.

---

### Post by Meiji on 2009-05-18
> I've never seen those exact Gparted error messages..."without assing" slot
lol well, it doesn't say exactly that.. it shows the message in Spanish, I literally translated it to English, but I don't know how it'd exactly say... Perhaps "No assigned" or something like that..

btw.. here the code:
```

meiji@meiji-desktop:~$ sudo fdisk -l
[sudo] password for meiji: 

Disk /dev/sda: 61.4 GB, 61475807232 bytes
255 heads, 63 sectores/pista, 7474 cilinders
Units = cilinders de 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1a5d1a5

Device    Start     Begin      End      Blocks  Id  System
/dev/sda1   *           1        7474    60034873+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilinders
Units = cilinders de 16065 * 512 = 8225280 bytes
Disk identifier: 0xb661de26

Device    Start     Begin      End      Blocks  Id  System
/dev/sdb1   *           1        4962    39857233+   7  HPFS/NTFS
/dev/sdb2            4964       14593    77352975    f  W95 Ext'd (LBA)
/dev/sdb5            4964       10164    41777001    7  HPFS/NTFS
/dev/sdb6           10165       13616    27728158+   7  HPFS/NTFS
/dev/sdb7           14254       14571     2554303+  83  Linux
/dev/sdb8           14572       14593      176683+  82  Linux swap / Solaris
meiji@meiji-desktop:~$ 

```

> In future, you will find it much easier to do partition work using the GParted LiveCD instead of booting from the Ubuntu CD, because the GParted LiveCD doesn't mount any of the partitions. Also, it's a newer version than the one bundled with Ubuntu. You can get it from the distrowatch.com website.
Thanks Mark Phelps! That's a good tip! I'll get GParted Live CD asap! =)

---

### Post by logos34 on 2009-05-18
> **Meiji said:**
> lol well, it doesn't say exactly that.. it shows the message in Spanish, I literally translated it to English, but I don't know how it'd exactly say... Perhaps "No assigned" or something like that..

ah, I see...I should have guessed

> /dev/sdb6           10165       13616    27728158+   7  HPFS/NTFS

Hmm...it's NTFS formatted, but I can't think of a reason why it refuses to delete sdb6 if nothing inside the extended partition, sdb2, is mounted.  A problem with shrinking I could understand, but not deleting. 

Hopefully the Gparted live cd will succeed--it sometimes works where the version on the ubuntu live cd fails.

---

### Post by Meiji on 2009-05-18
When I right click on /dev/sdb6 inside GParted, and click on Information, it says it's not mounted.. I don't know if it's due to that, but it lets me suppress space from it and then assign it to /dev/sdb7. Yerterday I made a little experiment with 10mb, and I succeded, then I tried with 100mb and succeded as well. Then I suppressed 5gigs, but when I was gonna assign them to dev/sdb7, GParted suddenly close O.o ... It was pretty late though.. so I decided to stop for that day and continue another =P ..

---

