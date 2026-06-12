---
title: "installing onto LVM"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by mikereed on 2008-12-12
Hi,
Last year I installed 7.10 and used the alternate CD to setup LVM on some RAID disks.  From reading various posts this does not seem uncommon. Everything went OK and since then I have upgraded to 8.04 with no problems.
I now wanted to try 8.10 with a fresh install i.e. not upgrade my 8.04.  So I downloaded the 8.10 alternate CD and was planning to run it and use it to create a new logical volume into which I could put the fresh 8.10 installation.  And this is where the problem is.  Although my original 7.10 installation allowed me to set up LVM, a subsequent installation disk doesn't seem to be able to see the LVM setup created by the previous installation.  That doesn't seem very sensible.  Am I doing something wrong?
I messed around a bit and it looks like you don't get access to LVM software on the installation disk until you create a brand new physical partition and then setup LVM on it.  Of course, I'm worried about messing about to much because I don't want to risk my current 8.04 installation.
Mike.

---

### Post by mikereed on 2009-05-13
Thought I had already posted my solution to this but I obviously didn't submit correctly so here it is.

The irony here is that you use the CD that doesn't have LVM on it, that's right, you use the LiveCD.  In summary this allows you to boot without mounting your other disks, then install lvm on the system booted from the LiveCD, which now allows you to see your LVM setup, create your new LV, then click the "install" icon to install the new version into your new LV.  Of course, if you want a server version you will need to install that afterwards but there are lots of posts telling you how to do that. This is where I found the detailed explanation.

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

I obviously skipped some bits because I clearly already had /boot and other partitions setup.  I just needed to create one new LV into which I installed the new Ubuntu version.

As I said, it is ironic that to do an LVM installation onto a current LVM system you use the disk that doesn't have LVM :)

---

