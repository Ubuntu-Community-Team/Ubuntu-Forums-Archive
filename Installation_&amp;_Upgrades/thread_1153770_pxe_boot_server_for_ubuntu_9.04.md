---
title: "pxe boot server for ubuntu 9.04"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by vcba79 on 2009-05-09
Hi, all

I am trying to setup a pxe boot server on ubuntu. PCs boot from network can get ip,show menu,load kernel correctly at this time. Here is my menu definition:

default menu.c32

label ubuntu_desktop_amd64
        kernel ubuntu/9.04/amd64/desktop/vmlinuz
        append initrd=ubuntu/9.04/amd64/desktop/initrd.gz boot=casper netboot=nfs nfsroot=10.1.2.20:/u00/linux/ubuntu/9.04/amd64/desktop

This configuration never enter setup screen. I copied all desktop cd files to /u00/linux/ubuntu/9.04/amd64/desktop and other nfs client can access this directory. I guess there is something wrong about nfs. Is it possible to use ftp instead of nfs? If nfs is only option, how can I troubleshooting this problem?


Thanks,

Vincent Chen

---

### Post by cariboo on 2009-05-09
Have you had a look at Edubuntu, the server does just what you need, if I remember correcty it uses tftp.

---

