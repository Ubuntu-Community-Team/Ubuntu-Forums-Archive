---
title: "External HDD permissions/owner can't be changed?"
date: 2011-11-23
forum: Hardware
---

### Post by wesleycj on 2011-11-23
I have a Fantom external hard drive that I used as a backup from my old Apple OSX Snow Leopard computer.  It wasn't a time machine backup, just a dump for files I never wanted to lose.  
I'm somewhat familiar with Linux, and I've been trying to access these files.  The problem is, the owner is set to 99, and no chown commands I've tried will change the owner.  I no longer have access to any Apple computers.  

This is an example of what I've tried:
chown -R wcjessen:wcjessen /media/backup
It SAYS the owner changed, but it also says "read-only".  Also, when you go back and check on the files, they are still user 99.  

I can open the files if I right-click on them and "open as admin".  I can't save them or anything, but I can technically view them. 

I'm sorry, this is about all I can give you with my limited knowledge.  If there's any important info I can provide, please provide some basic instructions.  Thank you very much!

---

### Post by gabrielaca on 2011-11-23
hi wesleycj, i had the same problem but marinara and usksider helped me out, read my post:

> [http://ubuntuforums.org/showthread.php?t=1882468](http://ubuntuforums.org/showthread.php?t=1882468)


Re: cant read/write to my USB HDD


I installed NTFS-3G with Synaptic Package Manager (NTFSPROGS was removed by Synaptic at the same time) and was immediately able to write to the USB drive, which I am currently using to back-up my system.

Hope this helps you too.

---

### Post by wesleycj on 2011-11-23
Thank you for responding!  Unfortunately, this didn't seem to solve the  problem.  I can write to the drive, but I can't pull many of the files  off of it.  

Sorry, I forgot to mention that SOME of the files aren't locked.  The  whole drive isn't the problem, just individual files and folders that I  can't access due to permissions/ownership.  I've tried changing  ownership for hours now, but nothing seems to take.

---

### Post by gabrielaca on 2011-11-23
sorry to hear that, maybe someone else can help you later.

---

### Post by coffeecat on 2011-11-23
> **wesleycj said:**
>  I can write to the drive, but I can't pull many of the files  off of it.  

Sorry, I forgot to mention that SOME of the files aren't locked.  The  whole drive isn't the problem, just individual files and folders that I  can't access due to permissions/ownership.  I've tried changing  ownership for hours now, but nothing seems to take.

Are you sure you can write to the drive? If you can write you should be able to chown, **if** the filesystem supports Unix permissions. My guess is that your drive is formatted with the journalled version of hfs+, the MacOS fileystem. You can mount the journalled version read-only in Ubuntu, but you can mount the non-journalled version read-write. The MacOS Disk Utility defaults to the journalled version of hfs+ which is why I am surprised you say you can write to the drive from Ubuntu. (In point of fact, you can mount a journalled hfs+ drive read-write with a force option, but I would not recommend that.)

If your drive has the non-journalled hfs+ filesystem, a few chmod commands might help, but the easiest thing in the long run is to use a root Nautilus file browser, opened with:

```
gksu nautilus
```

But before you do that, please confirm a couple of things. Was the drive formatted in MacOS with a Mac filesystem? And are you trying to access it from a permanent hard drive installation of Ubuntu or from the live CD? I'm slightly puzzled by the UID of 99, which doesn't sound quite right for MacOS saved files. 

> **gabrielaca said:**
> I installed NTFS-3G with Synaptic Package Manager (NTFSPROGS was removed by Synaptic at the same time) and was immediately able to write to the USB drive, which I am currently using to back-up my system.

Point of information. In 11.10, the package ntfs-3g comes as default and includes the functionality previously provided by ntfsprogs which is why ntfsprogs is removed when you install ntfs-3g. However, if you had to (re)install ntfs-3g and remove ntfsprogs, you must have (possibly accidentally) installed ntfsprogs which is no longer needed. ntfs-3g is needed for read-write of NTFS filesystems which the OP's drive is unlikely to be formatted as. MacOS does not support write to NTFS out of the box. But good luck with using your NTFS drive, gabrielaca.

---

### Post by wesleycj on 2011-11-23
My humble apologies, it turns out I can't write to the drive.  I'm kind of a novice, so I appretiate the help here, and you taking the time to write all this.  

**OK, for the details: **
-Yes, it was formatted on this computer when it still had a working Apple OS.  
-I am accessing the drive from the same computer, but with a full install of Linux that takes up the whole drive.
-When I look at some of the folder/files on the drive that have a lock hovering over them, I get this:
"Owner:  99 - user #99"
"Group:  99"
And I have no read/write access.  I do have read access when I do a gksu nautilus, but it won't let me copy/paste even then. 
When I look at the disk in disk utility, it has two things: EFI, which is formatted in FAT32, and the main part of the drive, which is formatted in HFS+.

I could be doing my chown statements incorrectly.  It seemed like it was going alright, but this stuff is a little out of my league.

---

### Post by coffeecat on 2011-11-23
> **wesleycj said:**
> And I have no read/write access.  I do have read access when I do a gksu nautilus, but it won't let me copy/paste even then.

That is very odd. With a gksu nautilus browser, you should be able to copy and paste. The one problem with that is that it *might* change the ownership of the files to root on your Ubuntu hard drive, but that's easily dealt with by chowning.
 
> **wesleycj said:**
> When I look at the disk in disk utility, it has two things: EFI, which is formatted in FAT32, and the main part of the drive, which is formatted in HFS+.

That's a typical GPT partition layout, with a small EFI partition that appears to be FAT32. Nothing wrong there.

> **wesleycj said:**
> I could be doing my chown statements incorrectly.  It seemed like it was going alright, but this stuff is a little out of my league.

The chown command won't work on the hfs+ drive anyway if you don't have write access, so I wouldn't worry about that.

Which leaves us with gksu nautilus. Try a simple drag and drop instead of copying and pasting.

---

### Post by wesleycj on 2011-11-23
Using gksu nautilus, I tried to drag some of the folders to my own HDD.  I get this error: 
"Error while copying.  The folder "[One of the locked folders]" cannot be handled because you do not have permissions to read it."

I get the feeling Apple is really strict with permissions.  But at least I know not to waste my time with chown statements.

---

### Post by coffeecat on 2011-11-23
> **wesleycj said:**
> Using gksu nautilus, I tried to drag some of the folders to my own HDD. I get this error:
"Error while copying. The folder "[One of the locked folders]" cannot be handled because you do not have permissions to read it."

I get the feeling Apple is really strict with permissions.

That is weird. MacOS (and hfs+) uses the same Unix system of permissions as Linux, and you have root privileges with a gksu nautilus browser, so I don't understand why you are getting that error.

I won't be able to do anything for a day or more, but I'll format a drive journalled hfs+ with my Mac and see if I can reproduce this. I routinely use a non-journalled hfs+ formatted drive for transferring files between MacOS and Ubuntu, so I am able chown and chmod happily from both OSs with that. Because I don't usually use the journalled version, I may be missing something. I'll post back but possibly not for some time.

---

### Post by wesleycj on 2011-11-23
Hey, no rush.  Thank you very much for doing that!  
I will also be sure to post back if there are any developments, good or bad.

---

### Post by coffeecat on 2011-11-23
> **wesleycj said:**
> Hey, no rush.  Thank you very much for doing that! 

No problem! I'm a bit like Sherlock Holmes - I don't like unsolved puzzles. :)

---

### Post by coffeecat on 2011-11-26
Sorry for the delay, but I have some answers. First this:

> **coffeecat said:**
> I'm slightly puzzled by the UID of 99, which doesn't sound quite right for MacOS saved files. 

For some reason, I'd got in in my head that the default UID for a first created account in MacOS is 501. That was wrong. The first UID in MacOS is 99, so mystery no longer.

I'm able to (nearly) reproduce the problem you get with a gksu nautilus file browser. I formatted a spare drive journalled hfs+ with my Mac and copied most of the folders and contents of my Mac home folder onto it, and then mounted it in Ubuntu. With a normal nautilus file browser several folders, including Documents I was not able to open. With a gksu nautilus browser I was, but trying to copy a file from a Documents sub-folder led to "There are an error copying the file into.... Error opening file: Permission denied." A little different from the error you saw, and totally unexpected considering you have root privileges with a gksu nautilus. The permissions of the file I tried to copy were 715 which is really weird for a personal document. I suspect this might be something to do with it.

Anyway - two workarounds.

1 - Find a Mac-owning friend and change all the permissions globally.

Or...

2 - Use the terminal. If you:

```
sudo cp /media/mountpoint/path/to/file/filenames /home/yourname/wherever/
```

They will copy but will be owned by root, and you will have to sudo chown them all. Possibly sudo chmod as well if the weird permissions remain. Or you could "sudo -i" in the terminal to get a root prompt which will allow you to cd to all the difficult folders, and then use cp.

Also - if you copy your files to another hard drive or partition formatted NTFS, depending on the mount options, that will effectively "lose" the root ownership.

---

