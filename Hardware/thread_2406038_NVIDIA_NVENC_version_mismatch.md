---
title: "NVIDIA NVENC version mismatch"
date: 2018-11-14
forum: Hardware
---

### Post by cranerja on 2018-11-14
I am on Ubuntu 18.10, currently running driver 415 with a GTX 1080.

As per NVIDIA documentation,

Corresponds to Video Codec SDK version 8.2.16.   Minimum required driver versions:  Linux: 396.24 or newer  Windows: 397.93 or newer  

Yet whether I am on 396.24, 410.73, or 415.13 I get the following when using it in ffmpeg:

Driver does not support the required nvenc API version. Required: 8.2 Found: 8.1 

I can't get 8.1 to compile either, so I would rather just get this to work. Has anyone experienced this?

---

### Post by congtt2801 on 2018-11-15
Just using older ffmpeg's version: release/3.x.
Work for me with Ubuntu 16.04, Quadro P4000, Nvidia 415.13. FFmpeg 3.4

---

### Post by cranerja on 2018-11-15
While I progress past the other problem, it is still unusable. 
```
Error initializing output stream 0:0 -- Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height


```

However, no parameter changes affect the output.

---

