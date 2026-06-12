---
title: "Using LiveCD to backup Windows?"
date: 2008-09-06
forum: General Help
---

### Post by pbotros1234 on 2008-09-06
I just got a new laptop, and it currently only has windows on it. I was wondering if it was possible to simply put in an Ubuntu LiveCD, mount the NTFS Windows partition, tar the whole thing, and then save that on a separate hard drive as backup.

I know that this would be possible, but my question is that if I wiped the entire hard drive and repartitioned, would Windows be reinstalled if I just untarred the backup and booted?

Sorry if that didn't make sense :confused:

---

### Post by pbotros1234 on 2008-09-06
Code will probably be something like this:

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows
tar -xzvf backup.tgz /media/windows
```


If I ever need to restore this, just mount the non-linux partition into /media/windows, and untar it.

So, after I untar it, will windows boot and everything?

---

### Post by caljohnsmith on 2008-09-06
Just a thought, but doing that tar method will only archive all your Windows files, so it won't capture the boot sector of your Windows partition for instance. That means that if you wipe your HDD clean, repartition, and untar all your Windows files into a newly created NTFS partition, Windows certainly won't boot right away. The least you will need to do then is run "fixboot" from your Windows Install CD to get a working boot sector in the new Windows partition. And if your new Windows boot partition is not the same number partition as before, then you will have to modify "boot.ini" to use the new partition number. That may be all you would need to do to get your newly restored Windows to boot, but I could be overlooking something. 

To back up an entire partition, many people use the "dd" command, since dd will make a perfect byte-for-byte copy of the original partition, boot sector and everything. It is a true "image" of the original, not just a file copy. But again, if you then restore that image to a different partition, probably the boot sector will be valid but boot.ini certainly won't. 

Just some initial thoughts--let me know if you need any more details. :)

---

### Post by pbotros1234 on 2008-09-06
Oh I understand, it wouldn't boot, I figured something like that would happen. And I don't have my Windows Install CD anymore, so I don't think fixboot will be an option.

So if I want to use dd, then... with my windows partition as /dev/sda1, and with an external hard drive mounted at /dev/sdb1, could I use:

```
dd if=/dev/sda1 of=/dev/sdb1/backup bs=1
```

Would that work? And then when I want to restore it sometime else, I could just transfer this and change around the boot.ini?

---

### Post by wolfen69 on 2008-09-06
if you have a valid windows key for it, you can reinstall windows using someone elses disk. remember, you are paying for the key (license), not the cd.

---

### Post by caljohnsmith on 2008-09-06
> **pbotros1234 said:**
> Oh I understand, it wouldn't boot, I figured something like that would happen. And I don't have my Windows Install CD anymore, so I don't think fixboot will be an option.

So if I want to use dd, then... with my windows partition as /dev/sda1, and with an external hard drive mounted at /dev/sdb1, could I use:

```
dd if=/dev/sda1 of=/dev/sdb1/backup bs=1
```

Would that work? And then when I want to restore it sometime else, I could just transfer this and change around the boot.ini?
Actually, the command below would be better since there's no need to copy one byte at a time (bs=1), since the partition starts/stops on sectors which are 512 bytes. Also, the "of" directive you have would not work since /dev/sda1 is not a directory. The command below will also compress the entire partition to save space and save it to your desktop:
```
sudo dd if=/dev/sda1 bs=512 | bzip2 -c > ~/Desktop/sda1.img.bz2
```

---

### Post by pbotros1234 on 2008-09-06
Thanks! Yea, that makes sense. That should work perfectly.

But is there anyway I can exclude certain folders from the bzip or the dd? I can't find any options on the man pages for dd or bzip2 that would let me do this, but I'm no expert.

---

### Post by caljohnsmith on 2008-09-06
> **pbotros1234 said:**
> Thanks! Yea, that makes sense. That should work perfectly.

But is there anyway I can exclude certain folders from the bzip or the dd? I can't find any options on the man pages for dd or bzip2 that would let me do this, but I'm no expert.
I think you might be misunderstanding that dd command; it copies data directly from the HDD, on a sector-by-sector basis; in other words, its just copying the raw digital data, all the 1s and 0s from the drive. "dd" doesn't have any clue what the data is, whether it is part of files, folders, etc, so it can't exclude any particular file or folder. :)

---

### Post by pbotros1234 on 2008-09-07
Oh I thought that was it, but I guess I wrongly figured that if it copied it sector by sector it would somehow also get the folder and file names and all. I've only used dd to completely wipe my USB sticks, so not too much experience there I guess.

But does that mean the bzip2 file will be unintelligible if I unzip it to the partition or something? Or if I open up the bzip file, will I actually see folders and everything?

Oh and to solve my problem of excluding things, this should work right?:
```
sudo dd if=/dev/sda1 bs=512 | tar cvpj backup.bz2 --exclude=/path/to/folder1 --exclude=/path/to/folder2 --exclude=/path....
```

---

### Post by caljohnsmith on 2008-09-07
> **pbotros1234 said:**
> Oh I thought that was it, but I guess I wrongly figured that if it copied it sector by sector it would somehow also get the folder and file names and all. I've only used dd to completely wipe my USB sticks, so not too much experience there I guess.

But does that mean the bzip2 file will be unintelligible if I unzip it to the partition or something? Or if I open up the bzip file, will I actually see folders and everything?

Oh and to solve my problem of excluding things, this should work right?:
```
sudo dd if=/dev/sda1 bs=512 | tar cvpj backup.bz2 --exclude=/path/to/folder1 --exclude=/path/to/folder2 --exclude=/path....
```
Unfortunately your idea above to exclude folders is not going to work. Think of it this way: when you "dd" the entire sda1 partition, it treats the entire partition as a single file. So when you compress the output of "dd" and save it as bz2, the compressed "sda1_backup.bz2" contains only one file, namely your entire sda1 partition. There is no easy way to delve into that sda1 "file" and exclude files/folders until you decompress it and restore it to its original state. Does that make more sense?

---

### Post by pbotros1234 on 2008-09-07
Ah! Okay yea now that makes perfect sense. It just directly copies the data, and it'll just be one big chunk of data. Awesome, thanks! I guess I can just move all the stuff I don't want to backup off my computer, and then move it back later after the backup. Thanks a lot! :)

---

### Post by Slycat34 on 2013-01-02
Sorry for reviving an old thread, but I figured it would be best to start from here than from a completely new topic

> **caljohnsmith said:**
> ```
sudo dd if=/dev/sda1 bs=512 | bzip2 -c > ~/Desktop/sda1.img.bz2
```

I can see how this creates an exact copy of a partition and compresses to a single *.img.bz2.  However, how does one go about restoring?  For a windows system recovery they require an .img and cannot use .img.bz2 or .img.zip.  Would it be just the same way in reverse like below?
```
tar -xzjf /path/to/backup.img.bz2 | dd of=/dev/sda1 bs=4096
```

---

### Post by howefield on 2013-01-02
Sorry for closing an old thread, but I figured it would be best to start from a completely new topic than from here.

Feel free to start afresh, referencing this one if needs be.

---

