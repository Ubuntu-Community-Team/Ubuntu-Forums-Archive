---
title: "Yet another DVD question."
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by peryton99 on 2007-08-19
I have looked around and none of the problems on the board match mine.  

here is the problem.

I have a LG GSA-H62L raid DVD player.  I installed according to directions to get the DVD to play.  Without libdvdcss installed the player will play the FBI warning and say that I need libdvdcss installed to play the dvd.  

I install the libdvdcss program, then the movie player program  locks up and it locks up the dvd player. (Unable to unmount or eject the CD)

This problem also replicates with MPlayer, VLC, and Kaffeine.  Has anybody else ran across this problem?  and if so, what was the fix?

---

### Post by linuxwizard on 2007-08-19
First off you need more codecs to play DVD
libdvdread3

libxine1-ffmpeg (Also requires libmad0, therefore libmad0 will be installed automatically along with this package)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I would make sure you have all codecs installed than see if you have problems.
[https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)

---

