---
title: "/etc/sudoers is owned by gid 1010, should be 0"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by ultralame on 2009-05-20
I am running Ubuntu 8.10

This morning I ran "sudo apt-get upgrade" and something must have gone wrong.

right after running the upgrade, I tried to install something and I got:
    /etc/sudoers is owned by gid 1010, should be 0

Checking my files, I see that /etc/sudoers is root:root but everything else in /etc is root:7root.  Furthermore, root's GID is 1010 and 7root is 0 (not sure when or if that change was made).

Preliminary searching on the web indicates that I will not be able to change this without logging in as root; I cannot call su, and this being Ubuntu, I never created a root password/login.

So it seems my only option is to reboot into single user mode...

1) Is there any way to do that without physical access?  I can get to the box, but I have to bring my KB and screen into the garage to do so.

2) How can I reboot it in the first place?  I have ssh access, but I cannot call shutdown or reboot.  I would rather not hit the reset switch if possible.

Thanks!

---

