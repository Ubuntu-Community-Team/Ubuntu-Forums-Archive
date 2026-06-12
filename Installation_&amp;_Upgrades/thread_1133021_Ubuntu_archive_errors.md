---
title: "Ubuntu archive errors"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by HARTEngr on 2009-04-22
Hi,

I have been installing Gutsy (ubuntu 7.10 32-bit) for several months from 
a live CD and then installing several packages using Synaptic Manager. 

The last time I did this successfully was about 10-15 days ago. Today, I 
am getting all kinds of archive errors. Apparently, the locations of the
files that the Synaptic Package Manager goes to get them from have changed,
or else, the archive has not been updated properly. It seems to have been
modified in April 2009 for all the directories where I get the errors.

Here are some messages I get when I try to install g++  :

=======
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-16.61_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-16.61_i386.deb)
  404 Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]
=======

I checked at the above URLS. And sure enough, those files don't exist anymore!

Somebody please tell me where to get them from, or else how to modify 
the URL for the Synaptic Package Manager. 

This is catastrophic for me.  :(

Thanks.

---

