---
title: "Software RAID 10 Recovery"
date: 2011-04-04
forum: Hardware
---

### Post by chrisolof on 2011-04-04
Hello,

I've got an Ubuntu 10.10 server set up to run on a software RAID 10 with four hard drives.

In the last few weeks it has stopped responding twice.  Both times I had to hard-reset the server - as it was in a state of not responding to any input.

After the second hard reset the server wouldn't boot, and said it didn't have enough drives to assemble the array (the system files reside on the array).

I'm hoping to get my data back - I don't think the drives are faulty, but I think there's confusion in two of the drives' superblocks.

So here's where I'm at:
I'm running on the 10.10 desktop live cd, I've started the array forcefully using mdadm, I can see my files, but I can't access them.

This makes sense because the first two spots for hard drives in the array aren't currently filled and the two hard drives that should be there are marked as spares.  So the array theoretically contains half of the data at the moment.  The other half is tied up in those two spare drives, which are mirrors of one another.

So my main question at the moment is:  how do I get these two hard drives back into the /dev/md0 array in the first two spots?  Removing them and adding them back just places them in the spare position again...  Anyone have any ideas?

---

### Post by chrisolof on 2011-04-05
Solved!  I ended up stopping the md0 array, then creating a new array using the same four disks at /dev/md2 with the --assume-clean option.  As soon as that finished the new array automatically got mounted and my data was in front of me.

Here are the commands I issued:

```
sudo mdadm --stop /dev/md0
sudo mdadm --create /dev/md2 -v --assume-clean --level=raid10 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

I didn't do too much browsing around or experimentation with the files in that sketchy new RAID array - pretty much just copied them off to an external hard drive ASAP.  So far it seems like I've got everything.

This forum thread was quite helpful:
[http://www.storageforum.net/forum/showthread.php?t=5890#11](http://www.storageforum.net/forum/showthread.php?t=5890#11)

The poster there just zeroed the superblocks and recreated the array in the /dev/md0 spot.  I couldn't get the --zero-superblock option to do anything (I think it said "mdadm: Couldn't open /dev/sdb1 for write - not zeroing"), so I decided to try an alternate take on his method.

What I believe happened is the superblocks got overwritten with information for the new /dev/md2 array - and because there wasn't any corruption in the newly-written superblocks, all the drives got added in.  The --assume-clean option told mdadm not to screw with anything (as far as resyncing) - just assemble the array.

Note:  You may be able to use /dev/md1 for the location of your new array, if you try this method.  In my case I had two RAID 10 arrays - the one at /dev/md0 was the important stuff, and the one at /dev/md1 was swap.  So, in my case, the first untouched spot for a new array was /dev/md2.  If you only have one array then /dev/md1 might work just as well as /dev/md2.  I think the important thing is that the spot doesn't already contain an array.

I have to say that this and other bad experiences with RAID arrays has me completely dissuaded.  I'm reprovisioning my server with a single hard drive.  I've also learned that RAID arrays featuring redundancy (in my case two hard drives were used purely for data redundancy) are no substitute for regular, thorough backups.

---

