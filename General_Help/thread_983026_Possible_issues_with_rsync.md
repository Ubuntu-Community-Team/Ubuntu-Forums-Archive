---
title: "Possible issues with rsync ?"
date: 2008-11-15
forum: General Help
---

### Post by Dave_Connor on 2008-11-15
When I rsync several movies to my external drive it is able to copy the first film in minutes but when it moves to the second file it just pauses after writing 32 kilobytes. I ctrl+c and just use cp. But does rsync have issues with my hardrive ? I have fat32 on my external drives incase if I wanted to use them with windows. Is there anyway to see if rsync maybe running in the background because I heard alot of how rsync is very good tool with using for backup purpose's.

---

### Post by vanadium on 2008-11-15
fat file systems are limited in the size of files you can store. For movies, I surely would be using ntfs in your case, where you want to use the drive on a Windows system.

---

### Post by Dave_Connor on 2008-11-15
I checked again the file system is ntfs not fat32. But is there still this limit issues with rsync ?

---

### Post by vanadium on 2008-11-15
I would not expect issues with the rsync program. Does it really freeze? What can happen is that a copy operation appears fast at first while data is copied to the buffer before being effectively written to disk. Perhaps you should copy/paste the console output of a session here. If you were to cp multiple video files, would then the copy proceed fully?

---

### Post by Dave_Connor on 2008-11-15
Current output of the backup I am trying to do. Rsync has issues so far with me with handling more than one file.
Prison.Break.S04E08.The.Price.HDTV.XviD.avi
   205586432  56%    1.79MB/s    0:01:27
   366722114 100%    1.90MB/s    0:03:04 (xfer#1, to-check=1/9)
Prison.Break.S04E09.HDTV.XviD-LOL.avi
       32768   0%   90.14kB/s    1:07:48
Then I wait for a few minutes and still the transfer is still like above.

---

