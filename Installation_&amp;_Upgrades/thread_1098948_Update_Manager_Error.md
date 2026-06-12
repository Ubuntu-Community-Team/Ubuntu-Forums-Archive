---
title: "Update Manager Error"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by roland0702 on 2009-03-17
Hey everyone. 

My update manager is giving me the following error:

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libswscale1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libswscale1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch




Thanks in advance. :D

---

### Post by pwnprog on 2009-03-17
exact same thing is happening to me. has been going on since yesterday afternoon. i am using ubuntu 8.04, and this is the first time that update manager has ever acted weird

---

### Post by roland0702 on 2009-03-17
Oh yeah, I forgot to mention that I am also using 8.04.

---

### Post by zvacet on 2009-03-17
Try 

```
sudo apt-get update && sudo apt-get upgrade
```

or maybe is a server issue.

---

### Post by roland0702 on 2009-03-17
> **zvacet said:**
> Try 

```
sudo apt-get update && sudo apt-get upgrade
```

or maybe is a server issue.


It worked! Awesome. Thank you very much! That big red update arrow was distracting me from my homework. ;)

Cheers

---

