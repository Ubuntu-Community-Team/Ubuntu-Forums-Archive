---
title: "Resize EXT3-partition"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by i386DX on 2005-12-17
I installed Ubuntu 5.10 on a 5Gb EXT3-partition, I left the other 35Gb for Windows.

0 -> 34,xx Gb NTFS
34,xx -> 35 Gb SWAP
35 Gb -> 40 Gb EXT3

Now, i want to resize/move my linux-partition (by shrinking the ntfs-partition). I can shrink the ntfs and move the swap with partition magic 6.0, but it can't resize EXT3-partitions. I cannot find a program that can move and resize my ext3-partition.

So is it possible to make my linux-partition bigger without having to reinstall the whole thing?

---

### Post by Herman on 2005-12-17
Hello, i386DX, I don't think there is any way to move, shrink or enlarge a Linux partition using the Ubuntu install CD, QTParted or Partition Magic. However, I am quite excited about progress I've made with experiments using the 'copy data to another partition' option in the partitioner of the Ubuntu install CD. It's a useful tool for copying data from one partition to another that everyone seem to have overlooked. (As far as I know anyway). So far this idea looks very promising. It will work for ext3, but won't work for reiserfs partitions. It allows 'cloning' one partition to an equal sized or larger partition, but you can't copy data to a smaller partition with this. Basically, the plan goes something like this: I am shrinking my Windows partition first, with QTParted, as you have suggested doing with partition magic. I then use the Ubuntu installer to make a new (temporary) partition equal in size to the old 5.0 GB one, in the space made by shrinking Windows. I then 'copy data from another partition' into it, (from the old Ubuntu partition).  Then I exit the partitioner (abort the installation) and re-boot the Ubuntu install CD once again. I delete the old partition after that's done. This leaves me with a Windows and a Ubuntu partition of say 5.0 GB each on the first 10.0 GB of the disk. Then I create a new partition at the other end of the new free space, and larger than Ubuntu was before. For me this could be up to 20.0 GB, for you it might be 30.0 GB. You don't have to use it all if you don't want to, the size for your new Ubuntu partition is up to you. After that I 'copy data from another partition', (back again, from the temporary one into the larger partition this time). When that's finished I delete the temporary partition. Then I use QTParted (or partition magic) to expand Windows to fill the gap again. Then I can put back some of the files I took out of Windows and copied to a CD. When I'm done I can boot into both systems again and all my updates, tweaks, setttings and files etc, are all intact! :D This is a breif explanation, there are a lot of details I have left out for the sake of brevity, and because I'm still finalizing the testing of this to write a new 'How-To'. I've done this successfully a few times already, it's just getting the exact, detailed instructions for it correct and in the right sequence for a new 'How-To' that I'm working on now. Perhaps later today I might be finished that. If you are experienced with the partitioner, you may have enough ideas to do it by now, but [COLOR=Red]be warned: it is a little trickier than it sounds.[/COLOR] Otherwise, if you are not in a hurry, you might want to wait for the new 'How-To' to be ready. :D (Herman)

---

### Post by az on 2005-12-18
I would not recommend partition magic.

You cannot change the starting point of a partition.  You can copy it, thoughm (as just described).  If you shrink your ntfs partition and make a little more room than your etx3 partition uses, you can copy it there and then resize it to opccupy the whole remainder of the disk.  

You can do this using parted on the instller cd.  I am not sure if the live cd has the ntfs libraries to shink the partition but I know the installer cd does.

Boot the installer and let it detect your hardware.  CTRL-ALT-F2 to the shell and run parted from the installer ramdisk

Read the parted manual.  It is very straightforward.

---

