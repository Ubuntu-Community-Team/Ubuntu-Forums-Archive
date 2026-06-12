---
title: "As in Ubuntu 8.04.1, aptoncd does not work."
date: 2008-11-02
forum: General Help
---

### Post by Marcelo Ramone on 2008-11-02
As in Ubuntu 8.04.1, aptoncd does not work.
 I installedUbuntu 8.10 and then aptoncd, download additional programs, I do a additional CD with aptoncd , burn the CD, install Ubuntu 8.10 on another pc without an Internet connection, I try to install packages from the cd created with aptoncd, but the instalation fail! I can not install almost any software!
 Example:
 marcelo @ ubuntu: ~ $ sudo aptitude install gstreamer0.10-ffmpeg
Reading package list ... Made
Creating dependency tree
Reading the state information ... Made
Reading the extended state information
Initializing the status of packages ... Made
The following are packets ROTOS:
   libavcodec-unstripped-51
Will install the following packages:
   gstreamer0.10-libavformat52 ffmpeg libavutil49 (to) (to) (to) libfaac0
   libfaad0 (to) (to) libpostproc51
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4629kB file. After unpacking will be used 11.9 MB.
Not satisfied with the dependencies of the following packages:
   libavcodec-unstripped-51: Depends: liba52-0.7.4 which is a virtual package.
                             Depends: libgsm1 (> = 1.0.12) which is a virtual package.
                             Depends: libx264-59 (> = 1:0. Svn20080408) which is a virtual package.
                             Depends: libxvidcore4 (> = 1:1.0.0-0.0) which is a virtual package.
The following actions will resolve these dependencies
 Keep the following packages in the current version:
gstreamer0.10-ffmpeg [Without installing]
libavcodec-unstripped-51 [Without installing]
libavformat52 [Without installing]
 The score is -9863
 Do you accept this solution? [Y / n / q /?] And
Will not install, update or remove any packages.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y / n /?] And
Writing extended state information ... Made
Reading package list ... Made
Creating dependency tree
Reading the state information ... Made
Reading the extended state information
Initializing the status of packages ... Made
 marcelo @ ubuntu: ~ $
 aptoncd not install dependencies! :mad:

 PLEASE SEE SCREENSHOTS:
[http://img220.imageshack.us/my.php?image=avidemuxaf3.png](http://img220.imageshack.us/my.php?image=avidemuxaf3.png)
[http://img233.imageshack.us/my.php?image=ffmpegfz7.png](http://img233.imageshack.us/my.php?image=ffmpegfz7.png)
[http://img118.imageshack.us/my.php?image=gnomemplayer1rl4.png](http://img118.imageshack.us/my.php?image=gnomemplayer1rl4.png)
[http://img230.imageshack.us/my.php?image=gnomemplayer2yv7.png](http://img230.imageshack.us/my.php?image=gnomemplayer2yv7.png)
[http://img233.imageshack.us/my.php?image=gstreamer010pluginsbadaw2.png](http://img233.imageshack.us/my.php?image=gstreamer010pluginsbadaw2.png)
[http://img217.imageshack.us/my.php?image=gstreamer010pluginsbadmnu0.png](http://img217.imageshack.us/my.php?image=gstreamer010pluginsbadmnu0.png)
[http://img217.imageshack.us/my.php?image=gstreamer010pluginsuglyxe3.png](http://img217.imageshack.us/my.php?image=gstreamer010pluginsuglyxe3.png)
[http://img217.imageshack.us/my.php?image=gtreamer0el2.png](http://img217.imageshack.us/my.php?image=gtreamer0el2.png)
[http://img217.imageshack.us/my.php?image=gtreamer0el2.png](http://img217.imageshack.us/my.php?image=gtreamer0el2.png)
 This is a translation from Spanish. I apologies for the inconveniences.

---

