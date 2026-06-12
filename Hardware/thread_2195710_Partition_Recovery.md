---
title: "Partition Recovery"
date: 2013-12-26
forum: Hardware
---

### Post by alvin-fatpiggy on 2013-12-26
Hi this is my first post on this forum and I'm not sure if this is the right place for my problem. If it isn't please tell me!

So I used to run Ubuntu using Wubi and recently made the jump to install it as my main (and only) OS. I originally had 3 partitions on my hdd, and I meant to install it on the C:/ partition while keeping the other partitions as they were (storing files and stuff). Thus I only backed up my files in the C:/ drive. But apparently I didn't read the installation instructions clearly enough and I chose the 'erase disk' option (or sth like that) and my entire disk was wiped clean.

So how am I able to recover my stuff?

I stopped installing stuff since I realised this problem so most of my files should not have been written over yet. The only thing I have on my hdd now is the Ubuntu files, and I've installed Chrome and Unity Tweak tool before I realised the problem.

I've tried searching other forums and used testdisk but it didn't work for me. Most of the other problems described was that the drive space was unallocated and they could get their previous partitions back. But mine was written over(?) and so now my hdd has a single partition of 300GBs (all data gone) instead of the 3 separate 100GBs it had. Testdisk didn't work. 

I could try photorec but I've heard it does not support every extension and therefore I may not get some files back, and that it randomly names recovered files and put them in random folders, so you have to sieve through the lot and try to find out what belongs to what (which is almost impossible to me since there are like thousands of small programme files that doesn't really make sense to me).

Of course, the best scenario will be for me to rewrite/ return it to the previous state where the files are still in the respective folders and names, but I know that's almost impossible. So what's the best way to get as close as this?

Thanks for all your help.

---

### Post by raja.genupula on 2013-12-26
make your post simple , so that more can view it

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by alvin-fatpiggy on 2013-12-26
Out of the 3 methods listed, parted gives me a message that says the drive is read-only and installing gpart from the terminal gives me a message that the package is not available. And testdisk didn't work for me previously. How else can I solve this? Thanks for your help

---

### Post by Mark Phelps on 2013-12-26
> So how am I able to recover my stuff?

Well, first of all, you can NOT install to an existing Windows partition unless you (1) are using Wubi, or (2) reformat the partition to a Linux filesystem.  If you did install using the latter, then you effectively overwrote the Windows OS partition.

If the Windows files are what you want to recover, then read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

### Post by alvin-fatpiggy on 2013-12-26
> **Mark Phelps said:**
> 
According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

Thanks Mark for your help, but I was actually hoping for a free recovery method... are there any? Since I'm still a student and kind of broke now. And I'll probably have to buy a usb to sata (I think) cable that'll add to the cost as well, according to that method. Anyone one else can help? Thanks anyway!

---

### Post by alvin-fatpiggy on 2013-12-27
Is there any other way to solve this problem?

---

### Post by Mark Phelps on 2013-12-27
> **alvin-fatpiggy said:**
> Thanks Mark for your help, but I was actually hoping for a free recovery method... are there any? Since I'm still a student and kind of broke now. And I'll probably have to buy a usb to sata (I think) cable that'll add to the cost as well, according to that method. 

There is "recuva" -- a free MS Windows based file recovery app.  I've never used it, but other have and claim it works.

---

### Post by alvin-fatpiggy on 2013-12-27
> **Mark Phelps said:**
> There is "recuva" -- a free MS Windows based file recovery app.  I've never used it, but other have and claim it works.

Thanks for replying, but I'm using Ubuntu now and I'm afraid if I reinstall windows more files might be overwritten and lost forever. Do you have any suggestions for Linux tools?

---

### Post by oldfred on 2013-12-27
Did you do the deeper search with testdisk and you need to stop using the install. Only work from live installer.
The more you have used system the more it overwrites. Linux randomly writes to entire allocated space so each write may be over writing data anywhere on drive or your old partitions.

I have used photorec and yes it is a long process. I learned to add the file name into every text file or program I create. (and better backup procedures). Then recovery is a bit easier as they all have the name in them. 
Photos also have meta-data that help in setting new names. I had to do a lot of file compares and grep to check for certain data so I could sort my text files. Since my text files had been saved many times, photorec also found the old copies, so once I had sorted to have all the same file it had many versions. 

 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)

---

### Post by alvin-fatpiggy on 2013-12-28
Hi oldfred, yes I already did the deeper search and I was working from a live dvd, but it still didn't work. And yup I've stopped using that notebook temporarily. 
As for photorec, I don't mind the long process, it's more of the file naming and other programmes-being-unable-to-locate-system-files problems. I'd use that as a last resort if there's really no other way to return the partitions to the previous state (as much as possible). As for the renaming you mentioned, is it only available for jpg files or any extensions?

Thanks. If anybody else has any other ways to restore the partitions and files please help! Thanks!

---

### Post by oldfred on 2013-12-28
Mark Phelps's suggestions have worked better in at least some cases. As users have reported that the Windows tools did find more data or worked well.  Not sure if they manage to find file names. I thought several of them would let you run them and see what it finds and only if it finds data then you have to pay to recover the data. And if it only recovers the same data as photorec you do not need them. So it may be time vs. money.

Only files with internal meta-data have a way to rename. If just text and you have no name then their is no way. Not sure if you can even restore much in the way of executables as it is hard to verify if correct or not.

---

