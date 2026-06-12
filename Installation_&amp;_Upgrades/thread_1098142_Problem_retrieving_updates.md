---
title: "Problem retrieving updates"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-03-16
I tried using synaptic to update the following packages but I get the following error:
> 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libswscale1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libswscale1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/ffmpeg_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/ffmpeg_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch

Anyone else having difficulty reaching repositories?

---

### Post by taurus on 2009-03-16
Go into System -> Administration -> Software Sources and switch to another server.

---

### Post by MaindotC on 2009-03-16
Thanks, taurus.  I've tried a couple but they're not updating.  I managed to locate deb's and manually install everyone except libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb and I'm having difficulty finding it on any of the servers in the server list.  Maybe it'll be fixed tomorrow.

---

### Post by kyphi on 2009-03-16
Same problem here.

Sit tight and wait for it to be fixed.

---

### Post by rosswmcgee on 2009-03-16
Same problem at 1746 pdt. Swithced to denver server and then back to usa server and the upgrades went through.

---

### Post by mrtomservo on 2009-03-17
I too received this error, it has happened before a few times.  I did what Taurus did, and switched from ubuntu.media.mit.edu server to the "MAIN" server, reloaded depository and the problem is fixed.  Must be a delay somewhere in the system for certain repositories getting updates.

---

### Post by MaindotC on 2009-03-17
I think I'm good.  I used the "choose best server" feature, which then decided I didn't need the ffmpeg file updated, and then I chose "Server from United States" and then it worked.  I guess the us.ubuntu.com or whatever it is is up now.

---

### Post by kyphi on 2009-03-18
> I think I'm good. I used the "choose best server" feature

Yes, of course you are good.  The world, however, is considerably bigger than the US of A (not meant as a criticism, folks - just a fact).

The updates came through after being assigned their proper sources - Medibuntu.

---

