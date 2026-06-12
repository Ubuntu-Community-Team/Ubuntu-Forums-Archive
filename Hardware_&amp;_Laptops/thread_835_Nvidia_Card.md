---
title: "Nvidia Card"
date: 2004-10-15
forum: Hardware &amp; Laptops
---

### Post by Termina on 2004-10-15
I downloaded the nvidia installer from nvidia.com, but it says I need the kernel source.

The only kernel source in the ubuntu respitories seems to be 2.6.7, while I'm using the 2.6.8 kernel. 

I'd hate to have to use an older kernel than what came with this.

This has always been my issue with Debian (never comes with the kernel source by default, like slackware does).  

Could anyone help me out? Thanks.  I'd like to play some games, but using the non-3D driver blows. ;)

---

### Post by ubuntu-geek on 2004-10-15
Termina,

Easy stuff... at a terminal prompt enter the following:

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

Reboot that will load and install the nvidia driver for you. 

For another reference here is the URL to the wiki:
[http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto)

---

### Post by jahLux on 2004-10-21
Thanks Ubuntu-Geek,
Now if only I can get the screen resolution/frequency issues resolved..... :?

---

### Post by jeffjj on 2004-10-24
That worked for me too! Thanks!!

---

