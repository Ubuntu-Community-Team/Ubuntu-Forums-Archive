---
title: "Partition size question"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by tklaus on 2009-04-05
I am setting up a dual boot with windows and I was wondering if these were ok partition sizes.

For swap 6 gb (I have 4 gb of RAM)

root 30 gb (I don't really know how much I need. Is this too much/little?)

home (I didn't know how much I would need for this or if I really need any at all)


Thanks for your help!

---

### Post by ninjapirate89 on 2009-04-05
If you already have 4 GB of RAM I wouldn't use 6GB of swap. You probably don't need any swap with that much actually.

---

### Post by tklaus on 2009-04-06
Oh ok. I guess I don't really understand how swap works. I just read somewhere that you where supposed to have 1-2 times as much as your RAM.

---

### Post by ninjapirate89 on 2009-04-06
"When your computer needs to run programs that are bigger than your available physical memory, most modern operating systems use a technique called swapping, in which chunks of memory are temporarily stored on the hard disk while other data is moved into physical memory space."

"It is possible to run a Linux system without a swap space, and the system will run well if you have a large amount of memory -- but if you run out of physical memory then the system will crash, as it has nothing else it can do, so it is advisable to have a swap space, especially since disk space is relatively cheap."

Copied these from here [http://www.linux.com/feature/121916]("http://www.linux.com/feature/121916") if you want to read it all.

---

### Post by blackened on 2009-04-06
What is the total size of the drive?

If you're giving /home its own partition, then 30Gb for the root partition is too much. Half that will likely be twice again more than you'll need. As an example, my old 8.10 root partition was created in late August and is still only 6Gb and some change.

Unless you just enjoy installing a ton of programs, then 15Gb for / should be more than sufficient.

The size of /home is gonna be a matter of personal taste. I usually keep a rather small home partition, but then mount/symlink other partitions and drives to subdirectories of my user directory. This method works well when sharing a drive with Windows as you can mount NTFS partitions/subdirectories to folders in your home directory as if they were there natively.

---

### Post by tklaus on 2009-04-06
The total size is around 160-170 gb. I allocated more back to my windows drive because that has a lot more media on it. The unallocated space has no file system, so should I just leave it like that?

---

### Post by anitha-h on 2009-04-06
for root(/) 10 to 20 gb is more than enough for desktop machines
since u have 4 gb u need not have swap or it is enough to have 4 gb swap
and the rest (or 40 - 80 gb) u can use for /home

---

### Post by blackened on 2009-04-06
> **tklaus said:**
> The total size is around 160-170 gb. I allocated more back to my windows drive because that has a lot more media on it. The unallocated space has no file system, so should I just leave it like that?

Yes, it'll be fine to just leave it unallocated until you do the install. As I hinted to in my last post, the filesystem in Linux is much more malleable than in Windows. You can pretty much create mountpoints anywhere in the filesystem (there are some limitations, but nothing like in Windows).

As an example:
You can mount subdirectories of other partitions into the main filesystem in a seamless manner. Say I have Windows on the first partition of drive A, call it sda1, and my home partition on the third partition of drive A, call it sda3, then I could mount the Windows folder /dev/sda1/Users/Trevor/Music to the folder /home/trevor/Music in my home partition and treat it as if it were just another folder in the filesystem.

---

### Post by tklaus on 2009-04-06
Ok I finally did it. I was so scared I was going to delete everything but it worked out fine. Both ubuntu and vista work and I am all set. I appreciate the help and advice!

---

### Post by linuxuser21 on 2009-04-06
> **tklaus said:**
> I am setting up a dual boot with windows and I was wondering if these were ok partition sizes.

For swap 6 gb (I have 4 gb of RAM)

root 30 gb (I don't really know how much I need. Is this too much/little?)

home (I didn't know how much I would need for this or if I really need any at all)


Thanks for your help!

If you have 4gb RAM, you actually don't even need much for Swap.  Swap is basically virtual RAM.  It takes that much of your hard drive and uses it as RAM.

---

