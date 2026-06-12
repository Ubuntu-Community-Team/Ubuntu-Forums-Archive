---
title: "java and gstreamer0.10-ffmpeg  install problem"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by alin19 on 2009-10-24
i have some problem installing java 

when i'm installing int from add/remove programs  or *sudo apt-get install sun-java6-jre*  i get:
[html]
W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  500 Internal Server Error

W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  500 Internal Server Error

E: Some index files failed to download, they have been ignored, or old ones used instead.

[/html]now i have installed a java using the binary version from here: 
[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)
and i run my aptana by runing [COLOR=#ff0000] ./AptanaStudio -vm '/usr/java/jre1.6.0_16/bin/java' 

[COLOR=Black]and  [/COLOR][/COLOR]gstreamer0.10-ffmpeg plugin has the same problem 
i'm puting them here because i think it is the same couse but i don't know it, need some help please;

i'm new to ubuntu, i have just replaced my windows 7 with ubuntu but it is a little hard untill i get used to it 
thanks guys
(i have also installed compiz,mozilla  thunderbird  and cairo dock, could those generate some conflicts?)
[html]W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg-debian/libavutil49_0.svn20090303-1ubuntu6_i386.deb
  500 Internal Server Error


W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg-debian/libavcodec52_0.svn20090303-1ubuntu6_i386.deb
  500 Internal Server Error


W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg-debian/libavformat52_0.svn20090303-1ubuntu6_i386.deb
  500 Internal Server Error


W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg-debian/libpostproc51_0.svn20090303-1ubuntu6_i386.deb
  500 Internal Server Error


W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg-debian/libswscale0_0.svn20090303-1ubuntu6_i386.deb
  500 Internal Server Error


W: Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.6.2-1ubuntu2_i386.deb
  500 Internal Server Error

[/html]

my ubuntu is version 9.04

---

### Post by alin19 on 2009-10-24
solve it (there was a problem with the ro server)

---

### Post by arvindshes on 2010-02-23
Internal Server problem still exists.

---

