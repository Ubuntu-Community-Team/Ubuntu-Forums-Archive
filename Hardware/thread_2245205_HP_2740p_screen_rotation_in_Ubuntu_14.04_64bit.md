---
title: "HP 2740p screen rotation in Ubuntu 14.04 64bit"
date: 2014-09-21
forum: Hardware
---

### Post by andy98 on 2014-09-21
Hi, I'm hoping that I can get some help solving the screen rotation for my tablet 2740p.
I found a link that supposely had solve the issue and maybe it did on another version of Ubuntu, but it didn't work for me. Here is the link:
[http://ubuntuforums.org/showthread.php?t=1588382](http://ubuntuforums.org/showthread.php?t=1588382)

So I attempted using the instructions specified in the post (link is above). Here are the steps I followed:

1. sudo add-apt-repository ppa:thjaeger/tabletpc
2. sudo apt-get update
On step 2, it failed to perform the update. Here is what I got:

W: Failed to fetch [http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

so I went to the site thjaeger and downloaded the .deb package for wacomrotate. Here is the link:
[https://launchpad.net/~thjaeger/+archive/ubuntu/tabletpc/+build/3884071](https://launchpad.net/~thjaeger/+archive/ubuntu/tabletpc/+build/3884071)

I manually installed the .deb package, but nothing is working. I restarted the computer and still no auto detection when I rotate the screen.

Any ideas?
Thank you in advance.

Computer: HP 2740P
OS: Ubuntu 14.04 64bit

---

