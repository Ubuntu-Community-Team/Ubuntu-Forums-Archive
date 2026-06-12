---
title: "make 1:1 copy of damaged HD for data restorage"
date: 2011-10-11
forum: Hardware
---

### Post by CryptKeeper777 on 2011-10-11
Some years ago, my external USB HD crashed. It didn't mount anymore. There were no too important data on it (mostly recorded movies and TV shows, nothing essential) and I didn't have any idea about data restoring etc., so I just put it away and bought a new one. 

Some days ago then, I accidentally partly overwrote the data storage partition on my current main USB HD (see [here]("http://ubuntuforums.org/showthread.php?p=11318364#post11318364"); problem solved). That's why I got a bit into data recovery and I read anywhere that it's possible to restore data from a HD that doesn't mount anymore (as long as it's still recognized when plugged in). That brought my old broken HD back into my mind, so I thought: Why not give it a shot and try to recover some data from it? Not much to gain, but at least nothing too lose and I may at least learn some stuff. 

I want to make a 1:1 copy of the HD on my 500 GB HD to be able to restore data then from an undamaged HD. I don't know anymore how big the broken HD is, either 250 or 500 GB, but for sure not more, so 500 GB is enough.

I found the command DDrescue which seemes to do pretty much exactly what I want. At least I thought so at first. But as far as I understand, I have to set up the partitions first the same way they are on the broken HD. That HD seems to have four partitions (sdX1-sdX4 in /dev when plugged in), but I didn't do partitioning myself back then when using the HD (at least as far as I remember), and I'm not even sure anymore which filesystem the HD has/had (maybe still the standard FAT32, but I was MacUser, so maybe I formatted it in HFS+). 

Then I googled for some information on dd which seems to be able to make 1:1 copies of HDs regardless of the filesystem. The problem is that I somewhere read that the two HDs (the broken and the recovery HD in this case) must be identical (same size, brand and whatever). Maybe they are even of the same size (though I don't think so), but definitely not identical apart from that (not the same model, not even the same brand). 

[B]What should I do? 

Once again in short:[/B]  I have a broken HD which is recognized when plugged in, with unknown size, partitions and filesystem, and an empty unbroken HD which is of the same size or bigger, but not the same model.

---

### Post by spiky001 on 2011-10-11
I dont think they have to be the same size etc Just the drive your cloning to mustn,t be smaller look [here]("http://www.backuphowto.info/linux-backup-hard-disk-clone-dd")

---

### Post by CryptKeeper777 on 2011-10-11
> **spiky001 said:**
> I dont think they have to be the same size etc Just the drive your cloning to mustn,t be smaller look [here]("http://www.backuphowto.info/linux-backup-hard-disk-clone-dd")
Then that only has to be the case when dd-ing operating system copies? I referred to the following statement:
> Using dd you can create backups of an entire harddisk or just a parts of  it. This is also usefull to quickly copy installations to similar  machines. It will only work on disks that are exactly the same in disk  geometry, meaning they have to the same model from the same brand.
I read through the (rather large) site ([click]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-dd.html")) not line by line but rather skimmed over it and this sentence caught my attention...

But I read the site you linked line by line, at least the first paragraphs, and dd seems to do EXACTLY what I want. Awesome! :-D

---

### Post by Gs Dewd on 2011-10-11
> **CryptKeeper777 said:**
> Then that only has to be the case when dd-ing operating system copies? I referred to the following statement:

I read through the (rather large) site ([click]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-dd.html")) not line by line but rather skimmed over it and this sentence caught my attention...

But I read the site you linked line by line, at least the first paragraphs, and dd seems to do EXACTLY what I want. Awesome! :-D

Please keep us posted on your progress. I too have a old 80 gig drive that has a bunch of setup files that crashed on me. I would love to be able to get the files off it.

---

### Post by westie457 on 2011-10-11
Hi the command below will 1:1 copy a drive to another.
Just remember to edit the first SDx to match the drive to copy and the second SDz to match the one to write to.
```
dd if=/dev/sdx of=/dev/sdz
```
All of the partitions will be copied as well including all relevant UUIDs.

An 80GB drive I did a few weeks ago took about half an hour so your 250GB drive will take about 2 hours. Have a meal and a coffee while the program is working.

If the drive cannot power up (spin) nothing free will help.

---

### Post by diasf on 2011-10-11
or you can 

dd if=/dev/sda1 of=file.iso

and then

mount -o loop file.iso /mnt/bla

or work with the iso itself to recover the data

---

### Post by CryptKeeper777 on 2011-10-12
I let it run over night (it took longer than 2h with about 10 kb/s), but I got this message in the end:
```
dd: reading `/dev/sdc': Input/output error
642088+0 records in
642088+0 records out
328749056 bytes (329 MB) copied, 27994.3 s, 11.7 kB/s

```
I restarted it now, but is just started to sound pretty ****** up and now I don't hear anything anymore... I think it may just have died. 

Whatever, as mentioned I had nothing to lose but now at least I know how to use dd. 

BTW for others using dd: It doesn't show any progress, and there's no option like -v either, but there's a trick: You have to open a new terminal and type the following:
```
 sudo killall -USR1 dd 
```, then a status message of the form above (without the first line) will appear in the terminal where dd is running. 

Thanks for all the help! And good luck to everyone who actually has important data to lose...

---

