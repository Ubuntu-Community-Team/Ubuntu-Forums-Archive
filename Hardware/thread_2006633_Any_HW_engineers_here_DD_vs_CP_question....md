---
title: "Any H/W engineers here? DD vs CP question..."
date: 2012-06-19
forum: Hardware
---

### Post by Moozillaaa on 2012-06-19
I have a fail**ed** partition / fail**ing** drive, and I need to know which command will be better to create a clone for recovery of the partition.

I will clone the entire drive, for recovery.

My concern is data [FURTHER] loss of the original, while I play with a clone.

I asked about cp vs. dd before, but it digressed into a "I never used 'x' command for that.

I hope only hardware experts will explain which would be better, IN INCREMENTAL DEGREE OF RISK.

'WHY' too, please?

---

### Post by Redblade20XX on 2012-06-19
What do you mean "failed partition"? Is the partition not working due to the hdd failing or the partition is corrupted while the hdd is failing?

Take a look at : [https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive](https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive)

DD is your best shot because it will copy the raw data including any damaged sector which you can screen out later.
CP will probably give you an error when it hits a damaged region.

-Red

---

### Post by Dngrsone on 2012-06-19
Seconded; dd will be your best bet, between the two.

---

### Post by dandnsmith on 2012-06-19
I agree that dd is the better approach.
However, be aware that using dd to clone the whole HDD in one go straight to another HDD carries its own perils - better to dd one partition at a time to either an image or to a partition (already made, and big enough) on the new HDD.

---

### Post by Moozillaaa on 2012-06-20
Title says it all here - how do I do this?

I clicked on a package link
help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive

and I get an association prompt.

Help?

---

### Post by Moozillaaa on 2012-06-21
Ok - ddrescue it is here.

But I have no clue how to launch it in a live environment.

apt-get install doesn't seem happy from LiveCD boot

---

### Post by Moozillaaa on 2012-06-21
ed.:
Not actually a file association prompt; rather a package manager prompt...

---

### Post by David Andersson on 2012-06-21
> **Moozillaaa said:**
> Ok - ddrescue it is here.


Be aware that there are **two** ddrescue in the repostitory, with package names "ddrescue" and "gddrescue". The "**gddrescue**" is the better tool. When installed the command is "ddrescue".

> **Moozillaaa said:**
> 
But I have no clue how to launch it in a live environment.

apt-get install doesn't seem happy from LiveCD boot

What happens when you try to install it? How much RAM does the computer have? Can you move the harddisk to another computer, where it becomes a secondary disk?

You run ddrescue like this. If you want the disk image in a file
```
sudo ddrescue --max-retries=1 /dev/sdXX IMAGEFILE.img ddrescue.log
```
or if you want to copy to a fresh partition
```
sudo ddrescue --max-retries=1 /dev/sdXX /dev/sdYY ddrescue.log
```
Replace sdXX with your faulty disk and sdYY or IMAGEFILE with the target you want.

It will copy the disk in at least two **passes**. First pass it will copy most of the data from large shunks of undamaged blocks. The second pass it will copy blocks near and around error areas. If you start ddrescue with option --max-retries=1 it will do a third pass trying to read faild blocks once again.

It takes time. Each pass might take several hours, depending on the number of faulty blocks and the size of the partition. If you have to stop the process in the middle, you can restart it with the exact same command, and it will continue where it were. That is what the log file is for.

---

### Post by cariboo on 2012-06-21
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Moozillaaa on 2012-06-21
:confused:

OK - I won't do it in the future, I have not done it now, and did not do it in the past.

Same subject? You must have gone to public school in United States.

:confused:

Thread 'a' is about data recovery on failing '**HARDWARE**'.

Thread '2' is about application operations in a live environment **Desktop Environment**.

If you don't mind too much, please UNmerge the threads. They are in NO way related, except for usage of the internet.

ed.:
In fact, you have REALLY made a mess of this. It is now a conglomeration of absolute gibberish, totally devoid of coherence.

The likelihood of help now is just about zero. THANKS.

---

