---
title: "[SOLVED] MEcoder not working."
date: 2008-10-13
forum: General Help
---

### Post by getfirefox on 2008-10-13
I have made a short animation in stopmotion (its on the repos) but when I try to export it useing the MEncoder a window pops up and says "Failed" and then it gives me this error:

```
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: /home/robert/.stopmotion/packer/Scene*
[mf] number of files: 1 (4)
VIDEO:  [IJPG]  0x0  24bpp  8.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:0x0  fps: 8.00  ftime:=0.1250
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================

Exiting...

```

Any help will be greatly appreciated thanks! :)

---

### Post by ju2wheels on 2008-10-13
Do you have ffmpeg properly installed?

```

sudo apt-get install ffmpeg

```

---

### Post by getfirefox on 2008-10-13
I ran that code and it said:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
I have reinstalled ffmpeg and it still won't work.

---

