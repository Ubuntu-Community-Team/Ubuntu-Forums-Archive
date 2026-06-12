---
title: "[SOLVED] altered my hard drive with e2fsck?"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by tonytux on 2007-10-01
ok i ran e2fsck on an older 20.4 GB Seagate Baracuda HD in the attempts to ensure it's current good state.  I read the e2fsck man page and decided to pass a few options, i decided on using ```
e2fsck -cFkp
``` This seems to have altered something with the geometry.  Previously I ran fdisk to create a basic linux bootable partition structure (1 part about 19 G as /, and an extended/swap part at the end). Now I go to do the same partitions and the numbers are different, the size is still 20.4 but I think the sectors or something changed.  Any ideas?

these are the options passed directly from e2fsck(8)
```
 -c     This  option  causes  e2fsck to use badblocks(8) program to do a read-only scan of       the device in order to find any bad blocks.  If any bad blocks are found, they are  added  to  the bad  block inode  to prevent them from being allocated to a file or directory.  If this option is specified twice, then the bad block scan will be done using a non-destructive read-write test.

-F     Flush the filesystem device’s buffer caches before beginning.   Only  really  useful  for  doing
 e2fsck time trials.

-k     When  combined with the -c option, any existing bad blocks in the bad blocks list are preserved, and any new bad blocks found by running badblocks(8) will be added to the  existing bad blocks list.

 -p     Automatically repair ("preen") the file system.  This option will case e2fsck  to automatically
 fix any filesystem problems that can be safely fixed without human intervention.  If e2fsck dis&#8208;
covers a problem which may require  the  system  administrator  to  take  additional  corrective
action,  e2fsck will print a description of the problem and then exit with the value 4 logically or’ed into the exit code.  (See the EXIT CODE section.)  This option is  normally  used  by  the system’s boot scripts.  It may not be specified at the same time as the -n or -y options.
```

---

### Post by Herman on 2007-10-01
> This seems to have altered something with the geometry. Previously I ran fdisk to create a basic linux bootable partition structure (1 part about 19 G as /, and an extended/swap part at the end). Now I go to do the same partitions and the numbers are different, the size is still 20.4 but I think the sectors or something changed. Any ideas?Well there are partitions which are listed (described) in our partition tables which is in the MBR or in extended partition tables for logical partititons.
It is the job of hard disk partitioning programs to work with partition tables and adjust them to the users's wants and needs. 
Partition editing programs deal with hard disk geometry. I have noticed that the same partitions, viewed with various partition editing programs, are not all recognized as healthy partitions by all partition editors.
I believe in sticking with the 'Parted based partitioners, that's my personal opinion, although Linux fdisk is good for looking and seems to agree with 'Parted based partitioners about what sectors should be the correct beginning and end points for hard disk partitions.
If you used Windows FDISK, however, then that is something else. You probably should not use Windows FDISK for making partitions for Ubuntu. Other commercial partitioners which are designed mainly for Windows only are best avoided as well,
Please post here the output from 'sudo fdisk -lu' so it's possible to see what you are talking about. (or a screen-cap from GParted or QTParted).
```
sudo fdisk -lu
```A file system is something that is created inside a partition. e2fsck, as far as I know, does not write to the partition table. I don't think it can.

You are on the right track to look up the man page for e2fsck and use your own common sense to make up your own customized command. You command looks okay to me, I would have skipped the -F option though. You have asked e2fsck to look for any bad blocks in your file system and report them in a list so that they will not be used, they will be ignored or skipped from now on. That should be good. Probably that's why the reported number of useful sectors is reduced, maybe it did what you wanted.
You also asked e2fsck to 'preen' your file system, which should also be good.

I have three e2fsck combinations I like, one is 'sudo e2fsck -C0 -p -f -v /dev/hda2' for preening. (on an unmounted file system, (use a Ubuntu Live CD or equivalent)).
```
sudo e2fsck -C0 -p -f -v /dev/hda2
``` Where: /dev/hda2 is my ext3 (Ubuntu) partition, otherwise replace 'hda2' with whatever partiion number is correct for you own partition arrangement.

For a more heavy-duty file system check, I use 'sudo e2fsck -y -f -v /dev/hda2' (on an unmounted file system)
```
sudo e2fsck -y -f -v /dev/hda2
```And for coping with bad blocks, I would use 'sudo e2fsck -c -c -k -v /dev/hda2' (on an unmounted file system)
```
sudo e2fsck -c -c -k -v /dev/hda2
```Those are my own personal preferences for e2fsck command combinations. I am not claiming they are any better than anyone else's, just that they seem to do the job well enough for me. I haven't tested the badblocks one as much as the others but it should work okay.

If you want to test your hard disk to see if it's healthy or on the way out and if it supports S.M.A.R.T. technology, I would recommend you try [smartmontools]("http://smartmontools.sourceforge.net/"). You should even be able to install that (temporarily) when running a Ubuntu LiveCD, through apt-get or synaptic package manager.
I installed it myself a few days ago but the hard disk in th computer I wanted to use it for was too old and didn't support S.M.A.R.T. But I have read good reports about smartmontools.

Another suggestion is to try the badblocks command 'sudo badblocks /dev/hda2' or something like that, (on an unmounted file system), 
```
sudo badblocks -n -v /dev/hda2
``` If that runs and does not report anything your hard disk is good. If it reports a lot of bad blocks then you hard disk might be on its way out. The badblocks test may take a long time. It would probably be normal for it to report just a few bad blocks.

Good luck with it and I will be interested if you reply back with any results or if you have more questions, thanks for the interesting question already,
Regards, Herman :)

---

### Post by tonytux on 2007-10-01
herman thnx for the quick response.  for the record, I don't use sindows or sindows applications (exceptions only apply to anoying things my wife needs for her win xp laptop, which is reduced to viewing some inet content or little games)

Anyways, just to kinda fill in the blanks, I'm actually gonna do a little [LFS]("http://www.linuxfromscratch.org/") system on a seperate hard drive and was preparing it for the install. 
sudo fdisk -lu outputed the fallowing for the aformentioned HD:
```
Disk /dev/sdc: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders, total 39851760 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1    39343184    19671592   83  Linux
/dev/sdc2        39343185    39841199      249007+   5  Extended
/dev/sdc5        39343186    39841199      249007   82  Linux swap / Solaris

```
now the original heads was like 16 and I believe the cylinders were alot higher, i don't remember the original number, I'll have to check the sticker to be able to reset to the original value or something

I did run cfdisk on this drive since (to create the partitions) and ran e2fsck to the point where it is now 0.0% non-contiguous, where it was like 9.something non-con...

previous to the original command of e2fsck -cFkp when I partitioned I would only get 605 unallocated sectors and now I have 10684 unallocated sectors, which I know is not so good.

---

### Post by Herman on 2007-10-02
> herman thnx for the quick response. for the record, I don't use sindows or sindows applications (exceptions only apply to anoying things my wife needs for her win xp laptop, which is reduced to viewing some inet content or little games):) Oh, okay, good.
>  Anyways, just to kinda fill in the blanks, I'm actually gonna do a little [LFS]("http://www.linuxfromscratch.org/") system on a seperate hard drive and was preparing it for the install.  Hey wow! I'd really be interested in trying that too, to see how much I can learn! Great! :)
>  sudo fdisk -lu outputed the fallowing for the aformentioned HD:
     Code:
     Disk /dev/sdc: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders, total 39851760 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1    39343184    19671592   83  Linux
/dev/sdc2        39343185    39841199      249007+   5  Extended
/dev/sdc5        39343186    39841199      249007   82  Linux swap / Solaris 
now the original heads was like 16 and I believe the cylinders were alot higher, i don't remember the original number, I'll have to check the sticker to be able to reset to the original value or something
 Well that fdisk output looks fine to me, nothing at all wrong there that I can see. I wouldn't worry about where it saya 255 heads, All fdisk outputs say that. It doesn't matter, it just the way fdisk chooses to add up the 'fake' disc geometry. 
> I did run cfdisk on this drive since (to create the partitions) and ran e2fsck to the point where it is now 0.0% non-contiguous, where it was like 9.something non-con... Hmmm.. In my opinion you are worrying too much and being too fussy,  :)
> previous to the original command of e2fsck -cFkp when I partitioned I would only get 605 unallocated sectors and now I have 10684 unallocated sectors, which I know is not so good. What sort of output do you get from 'sudo dumpe2fs -b /dev/sdc1' then?
```
sudo dumpe2fs -b /dev/sdc1
``` That command is supposed to list all the blocks which are reserved as bad in your file system.
In my filesystems I get a blank output like this:  ```
herman@amdxz:~$ sudo dumpe2fs -b /dev/sdb1
dumpe2fs 1.40-WIP (14-Nov-2006)
```
Here is an interesting link that I found just the other day, all about hard disk drives,[ http://www.storagereview.com/guide/index.html]("http://www.storagereview.com/guide/index.html")
CAUTION: That link leads to more links which lead to more links, which lead to more links....

Bye for now,
Regards, Herman :)

---

### Post by tonytux on 2007-10-06
Herman, you're right, I am over worrying about little things (darn obsessive compulsiveness kicking in....).  I went along with the LFS install, it's going good and I'm learning things.  That's the main objective.

I ran that sudo dumpe2fs -b /dev/sdc1 that you suggested and it came out blank as well.

And I'll check into that line of links you suggested, I'm sure I'll find something interesting through there, always looking to learn new things, even if it does mean going through like 30 pages of more links....

---

### Post by Herman on 2007-10-07
Okay, good then, tonytux,
I'd say your hard disk is probably okay then, for a whle at least. The best way is to use it, probably, and see what happens. :) Good luck with it, I hope it keeps going well for you for a long time. 

I'm going to read that link again too, there's a lot of reading in it, but it's all interesting, to me at least.
Bye for now, 
Regards, Herman :)

---

