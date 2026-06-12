---
title: "Hard drive partitions no longer needed"
date: 2012-11-24
forum: Hardware
---

### Post by syerges on 2012-11-24
I've read other posts and think I know the direction to take but I want to be as clear and concise as possible before I move forward as I don't want to lose my Ubuntu setup.

1. I have 1 partition Unknown - empty - bootable - dev/sdb1 : This was my Windows boot part of my hard drive that I want to add to my linux if possible. It doesn't give me an option to mount it, I'm guessing I have to format it and change the type.

2. Extended - Container for logical partitions - 68GB of memory - dev/sdb2 : I believe this is the Ubuntu OS and it is way too big for what it does. I want to make it a more reasonable size or get rid of it all together. Also can't mount this partition.

3.  Filesystem - Linux - Ext2 - sdb6 : I can mount and unmount this drive so It leads me to believe this is where my linux usable files are, where I want to add the free space.

4.  Swap space - Linux Swap - 6GB - dev/sdb5 : This is also probably extremely excessive unless it is where my operations are performed that help RAM as I convert Blue Ray DVD's... then it can stay that way.

I have another hard drive hooked up where I keep everything I want to save so my question is, are my assumptions of the drives accurate and is it safe to format/change the types and what type is best as I am completely done with Windows?


Thank You to all of you extremely helpful people in advance if I forget to thank you after your help!

---

### Post by mikewhatever on 2012-11-24
If you have all the important files backed up, and the goal is to format the first hdd (/dev/sda), then it's probably safe to preceed. Changing the existing partition types would make no sense, since you are going to format them anyway. As for the new partition, it depends on what you want them to be and what for.

---

### Post by ahallubuntu on 2012-11-24
First of all, what are the sizes of these partitions and for what purpose are you trying to shrink them?  Are you trying to make room for something?

What's the output of

```
sudo fdisk -l /dev/sdb
```

Also, what are the contents of your /etc/fstab file?

There's no point in deleting small partitions to try to add space.  Just leave them alone unless you have to remove them for some other reason.

If you get rid of the extended partition, you'll get rid of all the logical partitions inside of it.  Do you need ANY of those logical partitions inside the extended?  If so, you can't just blow away the extended partition.  It's the "container" for all logicals.

The purpose of the swap partition is to improve operating system performance.  The size was probably based on the amount of RAM your have (let me guess: 4GB?).  There was an old rule of thumb that says you make your swap 1.5X the size of your RAM, but that doesn't necessarily apply anymore.  So you probably COULD shrink the swap partition but I wouldn't get rid of it entirely.  Still, again, for what purpose are you trying to shrink it?  If it's at the end of your drive, you'd have 6GB at the end of the drive.  How are you going to use that?  You'd probably need to combine it with other free space - perhaps freed up by shrinking/removing other partitions on another portion of the drive.  If they aren't adjacent, then you'll have to do a lot of (time consuming) moving of these partitions.  Otherwise, it's a waste of time to create an orphan 6GB of free space somewhere.

As for the other Linux partitions: don't go blowing them away willy nilly if you still want to boot Ubuntu.  That ext2 partition may be a boot partition; blow it away and you won't be able to boot Ubuntu at all.

---

### Post by syerges on 2012-11-26
Thanks for the advice! After reading it, I just changed the boot partition that I previously had Windows installed on to something Linux could use and mount easily and left the rest alone. I really only needed somewhere to temporarily store my movies while transcoding them to something my Directv boxes could play. With young ones, I'm sick of repairing/replacing the discs. I unfortunately bought a cheap hard drive to store the movies and looked at reviews after the fact to find that the drive isn't fond of writing and removing files, so I only want to write if it is ready to stay there. Hopefully this way the storage hard drive holds up.  The extra knowledge is also important to me. 

Again, Thank You.

---

