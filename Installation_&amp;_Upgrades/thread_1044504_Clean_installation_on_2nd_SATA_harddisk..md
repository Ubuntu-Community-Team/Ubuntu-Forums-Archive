---
title: "Clean installation on 2nd SATA harddisk."
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Chame_Wizard on 2009-01-19
In reference to [this post]("http://ubuntuforums.org/showthread.php?t=1044406"),i have a question.

On my 1st disk(250 GB SATA,WD),I have Gutsy Gibbon and XP SP2(games only) installed as dual-boot.

However,I want to clean install Intrepid Ibex on my 2nd SATA HDD(which will be 500 GiB,also WD),so that it will be my main OS to use.

1.So will it bring any problem when install?And will GRUB give me an error?#-o

2.How can I make a 50/50(meaning 2x 250 GiB)partition of the new HDD,when there isn't a partition tool in the live cd?

3.What do I need,if I can/want move all files of my 1st HDD to my 2nd one?

:redface: :oops:

---

### Post by taurus on 2009-01-19
1.  Intrepid will install a new copy of GRUB to MBR so you can boot all three:  intrepid, hardy, & windows.

2.  Which LiveCD you are using because there is one in System -> Administration.

3.  You just have to mount the partition where hardy is.  Then, you can access it and copy whatever you want to your new harddrive/partition (intrepid).

---

### Post by Chame_Wizard on 2009-01-19
> **taurus said:**
> 1.  Intrepid will install a new copy of GRUB to MBR so you can boot all three:  intrepid, hardy, & windows.

2.  Which LiveCD you are using because there is one in System -> Administration.

3.  You just have to mount the partition where hardy is.  Then, you can access it and copy whatever you want to your new harddrive/partition (intrepid).
aha OK,
BTW,I don't have Hardy,but Gutsy.:tongue:

Right now I am using Intrebex live cd to test,but which one is it?:confused:

---

### Post by taurus on 2009-01-19
> **Chame_Wizard said:**
> aha OK,
BTW,I don't have Hardy,but Gutsy.:tongue:

Right now I am using Intrebex live cd to test,**but which one is it?**:confused:

Which one is which?  Are you asking about which harddrive is which?  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That would be a lower case letter L, not number 1.

Normally, the first harddrive is known as /dev/sda while the second harddrive is /dev/sdb.

---

### Post by Chame_Wizard on 2009-01-19
> **taurus said:**
> Which one is which?  Are you asking about which harddrive is which?  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That would be a lower case letter L, not number 1.

Normally, the first harddrive is known as /dev/sda while the second harddrive is /dev/sdb.

I know that(will remember the code),but i wasn't talking about the terminal.:tongue:

So how come there isn't any visible partition tool in the live CD?:confused:


my 1st SATA disk

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42954294

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15358   123363103+   7  HPFS/NTFS
/dev/sda2           15359       24781    75690247+  83  Linux
/dev/sda3           29806       30401     4787370    5  Extended
/dev/sda4           24782       29805    40355280   83  Linux
/dev/sda5           30027       30401     3012156   82  Linux swap / Solaris
/dev/sda6           29806       30026     1775119+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by taurus on 2009-01-19
Your second harddrive, external one (500GB), doesn't even show up.  Have you used or accessed it from windows before?

What's the output of this command from a terminal (make sure it is on and plugged in)?

```
dmesg | tail
```

---

### Post by Chame_Wizard on 2009-01-19
> **taurus said:**
> Your second harddrive, external one (500GB), doesn't even show up.  Have you used or accessed it from windows before?

What's the output of this command from a terminal (make sure it is on and plugged in)?

```
dmesg | tail
```

the 2nd HDD will be a SATA(internal HDD),i am asking now so that i am prepared.:tongue:

I also have a external one(250GB).

---

### Post by taurus on 2009-01-19
So basically you have not connected your second harddrive (internal) to your machine, yet.  Then, it wouldn't show up at all, not until you connect it to the mobo.

---

### Post by Chame_Wizard on 2009-01-19
> **taurus said:**
> So basically you have not connected your second harddrive (internal) to your machine, yet.  Then, it wouldn't show up at all, not until you connect it to the mobo.

That's true,so thanks for the advice.

where the heck is the thanks button?:confused:

---

