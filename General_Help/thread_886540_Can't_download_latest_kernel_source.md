---
title: "Can't download latest kernel source"
date: 2008-08-11
forum: General Help
---

### Post by BiscuitTin on 2008-08-11
Any ideas why I can't download the latest kernel source via git?

I'm doing as follows:

git clone git://kernel.ubuntu.com/ubuntu/ubuntu-intrepid.git ubuntu-intrepid

The command is just timing out after a couple of minutes and saying it can't open a socket:

root@tinman:/home/john/Src# git clone git://kernel.ubuntu.com/ubuntu/ubuntu-intrepid.git ubuntu-intrepid
Initialized empty Git repository in /home/john/Src/ubuntu-intrepid/.git/
kernel.ubuntu.com[0: 91.189.94.216]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)
fetch-pack from 'git://kernel.ubuntu.com/ubuntu/ubuntu-intrepid.git' failed.
root@tinman:/home/john/Src#

I've also tried downloading using either of these:

apt-get source linux-image-$(uname -r)
apt-get source linux-source

Both give me the wrong sources. I get 2.6.24.3 instead of 2.6.24-19.

---

