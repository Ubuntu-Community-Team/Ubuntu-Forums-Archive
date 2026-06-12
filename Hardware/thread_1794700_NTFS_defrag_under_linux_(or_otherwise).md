---
title: "NTFS defrag under linux (or otherwise)"
date: 2011-07-01
forum: Hardware
---

### Post by JC Cheloven on 2011-07-01
Hi, something trivial I'd like to share: 

A normal copy of files from an ntfs  disk to somewhere else (ie, another disk), deleting the files in the disk, and copying back the files to the original disk, has the effect of defragmenting the filesystem quite a lot. 

I tried with a 120Gb usb disk formatted as ntfs, which I've been using and using daily since years, and never had defragmented . These are the figures before and after, according to winXP defragmenting tool:

total fragmentation 32% --- 10%
files fragmentation 64% --- 21%
N of fragmented archives 99 --- 13
N of fragments in excess 3124 --- 971

The defragmenting tool reported "defrag needed" before, and "not needed" after. 
As this took noticeably less time than defragging using the win2 tool (as far as I can remember), I thought you may find it interesting.

Best
JC

---

### Post by varunendra on 2011-07-01
I had the same idea a few months ago, although I didn't try it under linux. I had a large partition (almost 240 GB) that was almost 80% full. It contained all kind of files from KB - sized tiny files to 7.4 GB ISOs and movies. There were only 4-5 large fragments that were part of an ISO and an MKV movie.

Having a good idea of the possible time the normal XP defragmenter could take, I decided to transfer all the data to an external drive, and then move it back. I also moved most of the smaller files to another partition to get almost 50% empty space to avoid any fragmentation while copying back. After moving the remaining files to the external drive, I even quick formatted the partition for extra guarantee of removing any partition table entries left behind. Now I had a picture of one contiguous block of files in my mind....

But to my utter surprise, when I moved back all the files from the external drive, they got aligned exactly as before - scattered all over the disk, with the same fragments of apparently same size and positions - just as if they weren't moved at all..!!

While I still don't understand how XP handles these file-manipulations, I thought at the moment - 'OMG! I should've done a full- format'. But unsure of success with this kind of weird behaviour and having already lost a lot of time, I didn't try again. Eventually I ended up doing the normal defragmentation (which obviously ran overnight ;)) which also compacted the files as I had expected with my move back and forth attempts.:)

Hope someone can explain this mystery with XP/NTFS..

---

### Post by JC Cheloven on 2011-07-01
Interesting, I'd also like to hear an explanation for that.

It must be that linux handles files in a diferent way than win2  in the ntfs filesystem. I copied to anoter ntfs disk BTW.

Also, it seems that the "or otherwise" bit in my title does not apply after all :)

---

