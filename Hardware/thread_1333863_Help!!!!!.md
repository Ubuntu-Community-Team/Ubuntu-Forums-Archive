---
title: "Help!!!!!"
date: 2009-11-21
forum: Hardware
---

### Post by aflog on 2009-11-21
I need help real bad!

I was just doing my thing in Ubuntu 9.10, Pidgin, Opera and Rhythmbox as you do. Then my computer just switched itself off. So I thought hmmm. I restarted it anyway, and the Ubuntu loading screen comes up and it wants to do file system scanning. It gets to 89% and then pops up with the black and white page saying "Cannot mount file system. Starting recovery shell". I'm sitting there thinking wtf. I didn't DO anything to it.

Anyway, I have no idea what to do at this shell, I'm at a loss. I'm running the LiveCD now in order to find out wtf is wrong with it. I ran the Palimpsest Disk Utility and ran a check on all my partitions. They all came up clean except the one with Ubuntu 9.10 on it. What does that mean and what should I do to get my desktop back?? I can mount the file systems fine while running the LiveCD, but that's about it.

Please please please any help??

Thanks

Jayden

---

### Post by aflog on 2009-11-21
Ok I managed to fix that using fsck.

Now I have another and even worse problem.

My /dev/sda2 cannot be mounted. Ill upload a screenshot of what the Disk Utility gives. Sorry it's not in English but if you need clarification just ask. 

Trying to use mount, I get:
> jayden@jayden-laptop:~$ sudo mount-t vfat /dev/sda2 /media/W
mount: wrong file system, false flag, incorrect super block
       on / dev/sda2, codepage or helper is missing, or other failure
       In some cases, useful information is found in syslog
       - Try dmesg | tail or something similar
 (it was translate by google).

Fsck gives this:
> jayden@jayden-laptop:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2:16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Super block is invalid, try to reserve blocks ...
fsck.ext2: Bad magic number in super-block while trying to open / dev/sda2

Super block could not be read or does not describe a correct
ext2 file system. If the device is valid and it really contains an
ext2 filesystem (and not swap or ufs or something else)
super block is broken, and you can try to run with an alternative
super-blocks:
    e2fsck-b 8193 <drive>


I really don't know whats wrong with it.*I have done nothing to it. I'm starting to get sick of 9.10 and the problems that have occurred since I upgraded. Is there any way I*can get the files off that partition onto another to prevent me loosing valuable files?

I await a reply, not to be ignored like usual, especially as this is vital.

Thanks

Jayden

---

### Post by aflog on 2009-11-23
As usual. No help. Im going back to 9.04 because it seems every ******* second time I try to boot into 9.10 one of my filesystems has been damaged and I'm kind of sick of losing everything and being stressed to redo my ******* homework without it crashing on me again.

Thanks UbuntuForums. I knew I could count on you.

---

### Post by Some Penguin on 2009-11-24
-----
sudo mount-t vfat /dev/sda2 /media/W
sudo fsck /dev/sda2
-----

There are situations where one of those commands makes sense.  There is absolutely no situation in which *both* of those commands make sense.  VFAT is for fat16/fat32 filesystems -- of the sort used by DOS and Windows 9x branches, for instance.   But you don't fsck a VFAT filesystem; fsck (really, e2fsck) is aimed at ext2 and the like, which are generally found in the Linux universe.

It's even more bizarre because the screenshot you attached cites *NTFS*, which is neither a VFAT type system (so you wouldn't do a 'mount -t vfat' on it and expect it to work), or an fsck (because an ext-type filesystem integrity check simply doesn't apply to non-ext-type filesystems).  Assuming that it's really NTFS and that you were simply confused with respect to the previous commands, you'd probably want to use an ntfs-3g driver so you get reasonably stable read/write access to it.  If you've mangled the partition table so it's labeled as NTFS but isn't really, well, it's not obvious, because you haven't said what it's supposed to be.

And you would probably receive more help if you labeled the thread with a meaningful subject that would lead people to quickly determine whether they could or could not provide relevant assistance, and if you didn't give three mutually exclusive indications of what the filesystem on /dev/sda2 should be without explaining which one it really is.

---

### Post by aflog on 2009-11-24
Hmmm.

1) I didn't notice it was saying it was NTFS, especially as the drive was meant to be FAT32 as that's what I format everything thats not ext3 as.

2) I didn't know fsck was only meant for ext3... so my bad.

3) Did I not put enough ! on the end of my topic title to make someone at least read the first post?

4) I went ahead and reformatted that drive anyway, I was sick of it causing problems. I've had nothing but problems since the upgrade to 9.10 and next time something with a harddrive goes wrong, I shall be going back to 9.04. Or maybe trying Fedora or Xubuntu. Shall see :)

Thanks for your reply anyway...

---

