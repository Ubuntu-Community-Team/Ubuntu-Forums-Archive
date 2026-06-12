---
title: "Assistance in recovering a HDD gone rampant"
date: 2009-05-03
forum: Hardware
---

### Post by Wydarr on 2009-05-03
Dear gentlemen, 
I have a 500 GB Iomega USB drive, that's a bit less than a year old, and who has an attitude problem. Basically, it has some bad sectors. The thing is that at least half the drive is good as new, while on the other half, I have no data, 'cos with the tools I amateurishly employed, I've never got past the first fault point.

So far with my limited (but ever-increasing due to this forum as well as others) knowledge I have tried the following on it, hoping to solve the problem:

I have used fdisk and mkfs.ext4. It stops writing and begins to do the equivalent of a man banging his head against the wall at inode no. 1724.
As we speak, I'm running:

sudo badblocks -vsw -p 3 -t random -o ~/iomega /dev/sdc

and so far, I get the following: 

Checking for bad blocks in read-write mode
From block 0 to 488386583
Testing with random pattern:  44.34% done, 8:44:04 elapsed

It's obviously stuck at that percentage (which is consistent with the previously mentioned inode (it was 1724 out of 3000+).

Next in line would be zeroing in the drive with dd. If this fails too, what can I do to detect and "mark" the bad sectors as bad, and continue to use at least partially the drive. 
Of course I'll put non essentials on it, but at least I'll get to use for a little bit more. 

Thanks for your help.

---

### Post by mikedep333 on 2009-05-03
I believe that a better method than zeroing the drive with dd is to use the "wipe" command with like 25 passes. That has fixed a bunch of drives for me.

Of course, in case you still have data on the other part of the drive, you will lose it all.

---

### Post by Wydarr on 2009-05-03
Thank you for your reply. 
I am not expecting to recover anything from the drive, hence the zeroing. 
I'll take the wipe option into consideration and will let you know of the result. 
In the meantime, if anybody has other ideas, I'd be happy to test them, since at this moment, the drive is unusable as it is. 
On the other hand, I was thinking of partitioning the drive into several parts: The first 40% as a whole (since I'm sure this area is OK), and from then on, experiment with various partition and test them separately. 
What I do not know, and I could use the help of someone more experienced hardware-wise than me is: are these bad blocks marked automatically, need I use the output file from the badblocks command when I create the file system with the mkfs.ext4 command, and once marked, do these corrupt and evil block remain marked for good, or I need to hold on to the log file for good. 
I appreciate your input and if it is deemed necessary at the end of this "journey" I'd be willing to write a small how-to on ways to attempt recovering the bad drives, as a part of the Ubuntu help repository.

---

