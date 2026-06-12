---
title: "lost partition, grub fails to load, nvidia issues"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by athianos on 2009-01-16
HELP!

So I had...

Vista on one extention
ubuntustudio on an ext3
64studio on a second ext3

Ubuntustudio failed to load after upgrade manager upgraded me.
I tried 64 studio. It failed to boot owing to Nvidia issues.

Ok.

So I logged on to VISTA for the first time in years. Decided to use their disk manager to salvage files and prepare a new space for a fresh install of... something. I've had trouble with 64bit installations. Perhaps a standard ubuntu install. I don't know.

Anyway, I wiped the second ext3 partition. 
Transferred my key files from the first ext3 to the second ext3.
Removed the first ext 3.
I couldn't resize the second ext3 partition for some reason so I rescanned the drives. 
Both ext3 partitions are not gone.

I restarted and Grub will not load. 

None of my livecds will load xserver.
The best I can get is a terminal prompt with no internet connection owing, i think, to NVIDIA problems.

I'd like to recover my files (testdisk?)
Ensure vista can load.
Prepare for a new install.

Please help!

---

### Post by caljohnsmith on 2009-01-16
How about first posting:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by athianos on 2009-01-17
Here goes

disk /dev/sda: 120.0 gb, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 bytes
Device Boot      Start      End     Blocks     id  system
/dev/sda1        63     16787924   8393931   27   unknown
/dev/sda2   *  16787925 75393044   29302560  7  HPFS/NTFS
/dev/sda3      75393045 234436544  79521750  5  Extended
/dev/sda5     232605198 234436544   915673+  82 Linux swap/solaris

I typed this by hand but I believe it's accurate. 

I had an sda7 I thought I was keeping somewhere in what appears to be sda3. I wonder whether windows ever actually recorded the change in partition I asked it to do, but deleted and moved data around anyway.

What's next?

(And thanks...)

---

### Post by caljohnsmith on 2009-01-17
To get Vista booting again, do you have a Vista Install CD? If so, boot that, go to the command line and do:
```
bootrec /fixmbr
```
And then you should be able to boot straight into Vista again. To recover your files, you could try using testdisk as you mentioned. You could download the Windows version of testdisk and try using it, it can be downloaded from [here]("http://www.cgsecurity.org/wiki/TestDisk_Download"). To use testdisk, once you start it up, how about following these instructions:

First choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

