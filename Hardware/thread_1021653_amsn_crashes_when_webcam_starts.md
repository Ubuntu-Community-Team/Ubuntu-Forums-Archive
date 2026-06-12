---
title: "amsn crashes when webcam starts"
date: 2008-12-25
forum: Hardware
---

### Post by civillian on 2008-12-25
On my eeepc (701 4G) I just installed eeebuntu 2.0 (based on ubuntu 8.10) core. I installed amsn (the only decent gtk based msn client with webcam support, imo) and when I was setting up the webcam and mic, it looked as if it was all going well.

At step one, the webcam was displaying fine, however after a minute or so of the app checking the drivers etc it crashed.

I launched it again fro the command line and when it crashed it displayed the following error message:

```
Not a JPEG file: starts with 0x68 0xad
Oops: malloc_video_bufs is 1 (expected 0) [utils/linux/capture/libng/grab-ng.c:malloc_bufs_check:235]
Oops: processes is 1 (expected 0) [utils/linux/capture/libng/convert.c:process_check:179]

```

Can anyone shed any light upon this problem for me at all?

Thanks a lot
Civ.

---

### Post by binbash on 2008-12-25
you should fill a bug report to amsn

---

### Post by Nerdriot on 2009-01-07
Having a similar issue. Must be a bug that will (hopefully) be fixed in a later release.

---

