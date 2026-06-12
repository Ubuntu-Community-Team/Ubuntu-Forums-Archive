---
title: "A First with Update Manager"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by pstefanini on 2009-03-16
While routinely downloading  four 'Important Security Updates".....  I got the following message:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch

 I have Ubuntu 8.04.  The updated programs are:

libavcodec1d
libavrformat1d
libavutil1d
libpostproc1d

Changes described as follows:

Version 3:0.cvs20070307-5ubuntu7.2: 

  * debian/patches/500_avcodec_check_pointers:
    - Check for existence of codec pointers before trying to deference
      them, fix a segmentation fault in xvidcap (LP: #207406).

Description of the updates as follows:

This is the demuxer library from the ffmpeg project. It supports most existing file formats (AVI, MPEG, OGG, Matroska, ASF...).
This package contains a Debian-specific version of the libavformat shared object that should only be used by Debian packages

Any idea what could be wrong?  Should I just uncheck them?  Thank you.  Phil

---

### Post by Partyboi2 on 2009-03-16
Try changing your download server in Software Sources.

---

### Post by archeryguru2000 on 2009-03-17
I believe the problem was on the server side.  I had the same problem yesterday... but today all is good.

~~archery~~

---

### Post by pstefanini on 2009-03-17
Thank you both... I tried to download but the same problem.  Then, I tried changing software sources... I removed the check mark next to  'Important Updates' and kept 'Recommended Updates' and 26 files downloaded automatically, no problem.  I'm still not sure why but it worked.  Thank you again!  Phil

---

