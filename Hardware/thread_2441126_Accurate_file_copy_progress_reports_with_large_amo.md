---
title: "Accurate file copy progress reports with large amounts of RAM?"
date: 2020-04-19
forum: Hardware
---

### Post by sorceror171 on 2020-04-19
I have a new machine that is, well, significantly overpowered. (Eight years since my last upgrade, wanted it relatively future-proofed, etc.) The system has a 3950x CPU, ASUS Crosshair VIII Hero motherboard, and - this is probably a key part of the issue - 64GB RAM. I'm running Xubuntu 19.10; this problem shows up in the Thunar file manager, but also in command-line utilities.

The progress of large file copies is not being reported correctly at all. For example, copying a file to an external USB3 flash drive, using rsync to check progress, I see:

```
time rsync -ah --progress 1.8GB-movie-file.mkv /media/username/VIDS/Video/
sending incremental file list
1.8GB-movie-file.mkv
          1.88G 100%  361.46MB/s    0:00:04 (xfr#1, to-chk=0/1)

real	11m38.860s
user	0m5.036s
sys	0m2.048s
```

The thing is, rsync sees the file copy complete within *four seconds*, since it's all going into the page cache in RAM. The actual write to the flash drive takes the remaining 11 minutes and 34 seconds, and there's no indication whatsoever of progress. Even iotop doesn't show much file I/O going on. I suspect this wasn't as much of a problem when RAM sizes were smaller (my previous system had 16GB of RAM) but with 64GB to play with the caching code is going wild with abandon.

Is there a good way to get a report of *actual* file copy progress when moving large files to external media?

---

