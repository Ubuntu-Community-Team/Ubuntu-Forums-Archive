---
title: "Data recovery, Recently Deleted File"
date: 2008-09-11
forum: General Help
---

### Post by jdorenbush on 2008-09-11
I just deleted a tar.gz file yesterday. It was an evolution-backup file. 

I did it from my laptop. My laptop is a Wubi installed Ubuntu system with Windows XP as well.

I put the tar.gz into the Trash yesterday and emptied it. I REALLY need it back. I was playing around with TestDisk, but I think I am in over my head.

I REALLY NEED THIS BACKUP. Any help would be extremely appreciated.

---

### Post by pytheas22 on 2008-09-11
You can try using photorec (it's part of the testdisk suite so it should already be installed; if not: 'sudo apt-get install testdisk').  Run it with:
```

sudo photorec
```

I think it's pretty intuitive to use, but if you're confused by something, ask.  Select the drive you want to search on the first screen, then choose "Intel" for partition type, and then you will be brought to the main screen.  At the bottom of the screen, go to "File Opt," and you can select which kinds of files photorec should look for--tell it to search only for .gz and .tar files.  Then go back to the main screen and select "Search" to start searching; hopefully it will find the file (it won't have the same name; you'll just have to search through all of the .tar.gz files that it finds until you find the one from Evolution).

testdisk is for repairing damaged partitions tables and things more than file recovery; you probably shouldn't be using testdisk.

Also remember not to install anything else onto your hard drive or move files around (in fact, you should really be running photorec from the live CD because running Ubuntu from the hard drive is bad) because it will decrease the chances that photorec can find and recover the file.

---

### Post by Thanoulis on 2008-09-11
In general ext3 filesystems (as the Ubuntu default) cannot recover deleted data...ext2 can though...so, good luck my friend! :)

---

### Post by jdorenbush on 2008-09-11
Photorec says its going to take over 2 hours to try and recover .gz and .tar files. We'll see what happens...

I don't have a Live CD. What is that?

If Photorec doesn't work am I out of luck?

EDIT: Ran out of storage space. It has recovered over 4000 .gz files and it had tons more to go. I don't know what to do. All the .gz files are named f10515152.gz or something along those lines. 

Is there no way to search for a specific file? or maybe from a specific date?

---

### Post by pytheas22 on 2008-09-11
A live CD is what most people use to install Ubuntu (you probably used wubi, I guess)--it's a CD that you can boot to and run Ubuntu, all from the CD (and install it if you want).

Unfortunately, I don't know of any way to tell photorec to search by date or size.  It would probably be possible, but I don't think there's a runtime option for it.  Your best bet is probably just to delete the recovered files manually as they come in (you can easily use the 'ls -a' command or arrange items by size in Nautilus to figure out which files are too small to be the one you're looking for), so that you won't run out of memory.

Also, if you have an external hard drive or something, you can tell photorec to dump the recovered files there so that you'll have more space.

---

### Post by jdorenbush on 2008-09-11
> **pytheas22 said:**
> Unfortunately, I don't know of any way to tell photorec to search by date or size.  It would probably be possible, but I don't think there's a runtime option for it.  Your best bet is probably just to delete the recovered files manually as they come in (you can easily use the 'ls -a' command or arrange items by size in Nautilus to figure out which files are too small to be the one you're looking for), so that you won't run out of memory.

I held of on deleting things because I assumed it would just screw things up even more. So whats the way to delete them without screwing up my recovery chances? You said, "manually". Can you tell me more? Thanks!

---

### Post by pytheas22 on 2008-09-11
Sure, I just meant that as the recovered files appear, you can delete the ones that you know aren't what you're looking for...in other words, every few minutes, go through what's been recovered and clean out whatever can't possibly be the file you want.  I call this 'manually' deleting them because it's the opposite of having photorec automatically delete or ignore recovered files that are not what you want (since there's no way to tell photorec to do that). 

Deleting them shouldn't hurt anything.  You should really be saving the recovered files onto external media, though, if at all possible--it's bad to be recovering them onto the same hard drive (or partition) where the file originally existed.

You can delete the files graphically if you like.  To do so, you will need to be root, so open Nautilus with:
```

sudo nautilus
```

and then navigate to the place where the files are being saved.  As I said, under the "View" menu in Nautilus you can choose to arrange files by size, so that should help you weed out ones that are too small to be what you're seeking.

You can also of course delete the files from the command-line with the 'rf' command.

---

### Post by jdorenbush on 2008-09-12
I am opening a bunch of these type of named files: f10515152.gz

And all thats inside of them is, a file titled the same as the .gz and the file type in Unknown. What the heck is all this stuff? I have thousands of them.

Also, if the evolution backup file is, evolution-backup.tar.gz should I be searching for .gz files or both, .tar and .gz??

---

### Post by pytheas22 on 2008-09-12
You probably only really need to search for .gz files.

photorec doesn't recover file names--it can only look for remnants of file headers and recover the associated files as much as possible; there's no way for it to know what the file was named.  So it generates random names like f10515152.gz (actually I think the numbers have to do with which sector of the drive it came from or something...but as far as you need to be concerned, they're random).

The file inside of each of the recovered files is probably the .tar (a .tar.gz archive is actually a .tar archive inside a .gz archive--it's two-dimensional).  Can you open any of the .tar files to see what's inside?  If it asks you which program to use to open them, choose Archive Manager.

---

### Post by jdorenbush on 2008-09-12
> **pytheas22 said:**
> Can you open any of the .tar files to see what's inside?  If it asks you which program to use to open them, choose Archive Manager.

When I try to either extract or open the file in the .gz file I get the following error:
```
An error occured while extracting files.
```
No space left on device.

That doesn't make sense though because I deleted just about every recovery file. There should be plenty of space left.

If the file isn't just a bunch of random numbers and letters it'll be a file called, changelog.Debian <-- I get that a lot.

---

### Post by pytheas22 on 2008-09-12
Are you sure that you really deleted the files (not just moved them to trash)?  There could also be issues because Gnome doesn't always delete stuff right away, even if you remove it from the trash.

If you have a flash drive or external USB available with free space, try copying over the files that you want to open to that and opening them there.

By the way, how big do you think the file that you're looking for is?

---

### Post by jdorenbush on 2008-09-12
> **pytheas22 said:**
> Are you sure that you really deleted the files (not just moved them to trash)?  There could also be issues because Gnome doesn't always delete stuff right away, even if you remove it from the trash.

If you have a flash drive or external USB available with free space, try copying over the files that you want to open to that and opening them there.

By the way, how big do you think the file that you're looking for is?

I moved the files to the Trash, then I emptied the Trash.

Well I backed up my most recent Evolution and it was like, 12-13MB.

---

### Post by pytheas22 on 2008-09-12
Could you open up the files after moving them to external media?

You may also want to read [this page]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html") about undeleting ext3 files.  It's complicated, but if photorec is not working for you, it might be your only option.

---

### Post by jdorenbush on 2008-09-12
> **pytheas22 said:**
> Could you open up the files after moving them to external media?

No :(

Just gave me the same error message.

I tried to Share a file and I wasn't even able to do that. I received another "Error was No space left on device". I've deleted just about all the contents that were Recovered thus far. I don't understand how I don't have space. Anything with any significant amount of space used on my Filesystem is the 3 following directories.

HOME - 3GB
USR - 2GB
PROC - 896MB

> **pytheas22 said:**
> You may also want to read [this page]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html") about undeleting ext3 files.  It's complicated, but if photorec is not working for you, it might be your only option.

Woah. That is fairly in depth. I am scared to even try. Lol

---

### Post by pytheas22 on 2008-09-13
It looks like you don't have that much space on your Ubuntu system to begin with--5 gigabytes is really the minimum and you're just above that--so that could be part of the problem.  You should still be able to move the .tar.gz files to somewhere else, though--like the Windows partition of your hard drive, or a floppy drive.  You don't need to share them using file sharing or anything; you should be able just to copy and paste them or something.

---

