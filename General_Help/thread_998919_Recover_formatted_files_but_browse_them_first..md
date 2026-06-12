---
title: "Recover formatted files but browse them first."
date: 2008-12-01
forum: General Help
---

### Post by bobbob1016 on 2008-12-01
I know people say to search the forums first.  I did, and got this [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
I booted a livecd and installed the three programs, gpart, testdisk, and parted.  However, I can't figure them out.  I have two identical drives, one that had data, another that didn't.  I want to figure out which one has recoverable data, since they were both reformatted, they both have "recoverable" partitions.  I tried in testdisk, but when I do "browse" I just get the generic file-structure, with lost+found.

Basically, how can I see my data, before recovering it?  I didn't write to the drive yet, apart from the formatting.

Edit:  The drive with the data was either ext2 or ext3 or fat32 beforehand.  90% sure it was either ext2 or ext3.

---

### Post by az on 2008-12-01
Foremost is a file carver.  You can run it in audit mode.  The only thing that will be written to the output directory is the file names of the files it will recovery.  

It won't be able to tell you the file names of the files as they were before the reformat, but you will get an idea of how many jpeg, mp3s, zip files... are found.

You don't need to try to recover the partition to do this.  It will work on the raw block device.  In this case, it will tell you which disk it is you want to work on.

---

### Post by bobbob1016 on 2008-12-01
> **az said:**
> Foremost is a file carver.  You can run it in audit mode.  The only thing that will be written to the output directory is the file names of the files it will recovery.

Do you have a suggestion as to which file carver?

Just to be sure I'm doing this right.  First I'd use the carver to show me the number of files that were formatted over.  Then testdisk or whichever to recover the files from the drive with the formatted data to the drive that was blank.

Edit:  I used scalpel from the repos, and had the output go to ~/scalpel-sdb/ and ~/scalpel-sdc/.  However, one says Unable to write output files, and the other is generating a list.  Would that mean that the one that is generating the list would be blank, and the other has files to be recovered?

---

### Post by az on 2008-12-01
> **bobbob1016 said:**
> Do you have a suggestion as to which file carver?

Just to be sure I'm doing this right.  First I'd use the carver to show me the number of files that were formatted over.  Then testdisk or whichever to recover the files from the drive with the formatted data to the drive that was blank.

Edit:  I used scalpel from the repos, and had the output go to ~/scalpel-sdb/ and ~/scalpel-sdc/.  However, one says Unable to write output files, and the other is generating a list.  Would that mean that the one that is generating the list would be blank, and the other has files to be recovered?

I meant use foremost - the file carver

sudo apt-get install foremost

mkdir recovery/directory
sudo foremost -w -i /dev/sdb -o recovery/directory

The -w arguments is for audit mode.  Scalpel is not very well supported and doesn't work as well as foremost of photorec.

---

