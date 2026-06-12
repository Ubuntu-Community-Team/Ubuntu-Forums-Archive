---
title: "Playing with ddrescue!"
date: 2013-07-08
forum: Hardware
---

### Post by quetzalin on 2013-07-08
Hello!,

I'm here to ask for tips and to know if the process i'm doing is right. 

The netbook fell to the ground while it was powered on, since then the HDD looks dead. I got the netbook hdd plugged into my computer, it's being recognized but from what i can see SMART reports a lot of errors and of course u can not access to it.

My goal is to recover as many files as i can (pictures mostly) or even repair the whole thing.

At the moment i'm running a ddrescue using another hdd i have (the original one is 250GB and mine is 500GB).
The command i'm using is *ddrescue -f -n -R /dev/hda /dev/hdb logfile* , it has been running for 3 days already and it says 173GB has been rescued so far with 183MB of error size. 

Now, the first question and something that bugs me is i was able to mount the hdb and it still has my old files!, how is that possible? shouldn't they be destroyed already?.

As soon as this ends i'm going to run the next command: *ddrescue -d -f -R -r3 /dev/hda /dev/hdb logfile* and finally try to recover using testdisk or photorec.

I have been thinking on starting over and using an image file instead of trying to do a disc-disc copy as im doing at the moment.

So what do u think / recommend?

Thanks a lot!

---

### Post by dino99 on 2013-07-08
you only might have (i hope so) a borked journal : why ?
- you can mount & reconize the device (thats very good)
- so run fsck/e2fsprog/tune2fs for checking errors (might have some broken inodes (quite normal with that bouncing laptop) and repairing them.

[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

---

### Post by quetzalin on 2013-07-08
I think i didn't explain myself right, i will try again :P.

The first ddrescue is still going on, it didn't finish. When i say *i was able to mount the hdb and it still has my old files!* i meant they are not the files im trying to rescue from the damaged hdd, they are the files i already had on that working hdd so if i still can mount and see the files on the target hdd it looks like ddrescue is doing nothing or maybe the -n option only creates that log file i need later for the second ddrescue command so maybe then it starts writing the info on the target hdd?.

Oh and, im working with FAT32 file system as that was the original file system on the damage hdd.

---

### Post by sudodus on 2013-07-08
I have used ddrescue, and it helped me save the contents from a disk. Only a small part of it was actually damaged. So I have confidence in ddrescue.

I cannot explain why you still see the old files on the target disk. I can only guess. I think the information is written as it should, but the operating system has not yet made the file browser (or terminal window and bash) aware of it. So it is getting information from some cache memory and showing it to you.

I suggest that you let ddrescue finish its work without disturbing it.

---

