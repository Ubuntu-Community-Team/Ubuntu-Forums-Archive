---
title: "Apt-mirror:  Jaunty does not like Hardy"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by howwhi on 2009-05-27
Good evening all,

I have two systems mirroring repositories with apt-mirror.  Both "work" and have functioned fine for some time now.  Both were originally built on Hardy (8.04) but recently a drive failure in a RAID gave me an excuse to upgrade one of the mirrors to Jaunty (9.04).

The Jaunty mirror builds fine.  I cloned the mirror.list file replacing each line of Jaunty with Intrepid and Hardy respectively trying to mirror all three Ubuntu releases.  The Intrepid mirror also builds fine.  Hardy gets sick all over the place.

These lines in the mirror.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse

yields this error
gzip: stdin: invalid compressed data--format violated
Unsuccessful stat on filename containing newline at /usr/bin/apt-mirror line 346, <STREAM> line 13.
Use of uninitialized value in split at /usr/bin/apt-mirror line 409, <STREAM> line 14.
Unsuccessful stat on filename containing newline at /usr/bin/apt-mirror line 346, <STREAM> line 15.
-- and they continue on for quite a while

For grins, I pulled the working Hardy mirror.list to run under Jaunty; much the same illness.

Is anyone successfully mirroring Hardy on a Jaunty server?  Am I Jinxed??

---

