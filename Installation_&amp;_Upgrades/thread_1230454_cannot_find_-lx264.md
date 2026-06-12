---
title: "cannot find -lx264"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by Fe++ on 2009-08-03
hi dear community,
                             I have installed ffmpeg and x264 following this procedure: [http://ubuntuforums.org/showpost.php?p=6963607&postcount=360](http://ubuntuforums.org/showpost.php?p=6963607&postcount=360). The folder with the respectively library (I don'y know why) are installed in /root/ by default. When I try to compile program that use that's library i obtain this error: /usr/bin/ld: cannot find -lx264.
libx264.a is in /root/x264. Obviously i've specified -lx264 at gcc and i've include this folder in the included directories of the gcc in netbeans.  Anyone have idea of the cause of error? What can I do? please help me. Thanks in advance.

---

