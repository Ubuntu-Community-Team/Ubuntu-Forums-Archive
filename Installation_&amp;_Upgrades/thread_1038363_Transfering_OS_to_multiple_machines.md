---
title: "Transfering OS to multiple machines"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by AndyP79 on 2009-01-12
Hi All,
 I have been experimenting for a while and seem to have a set up with Intrepid that I like. I would like to transfer this set-up to a new computer that i am wanting to build. How do I create my own "distro" ? 
I could always write down every little thing that I have done along the way, but would like to create a disk with all my goodies on it already.
Any word?
Thanks
-a

---

### Post by damphoud on 2009-01-12
You can look into Remastersys:

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by briandu on 2009-01-12
Do the following:

#On ur PC:
1)    dpkg --get-selections > pkglist.txt

copy file onto new installation (new PC) and then 
2)    dpkg --set-selections < pkglist.txt && apt-get dselect-upgrade

3)   You should bear in mind that you would also need to copy over configuration files from /etc when copying your system to a new computer.

This is fairly reliable and assumes the hardware is almost identical for step 3 to work otherwise leave step 3 out. (And I mean almost identical)

If u do step 1 and 2 the you will have to fine tune some of the params for the applications.

ANOTHER method is to is to use partimage and restore image onto second PC - BUT the hardware MUST be identical.

If u think that u can can "clone" from PC to PC u will be disappointed. Exacting requirements are needed with high tech knowledge. U R warned here.


Best advise: rather manually install per PC if any differences. Steps 1 & 2 work great for this.

Cheers.

---

