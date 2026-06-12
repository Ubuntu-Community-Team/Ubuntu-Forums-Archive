---
title: "apt-get upgrade stuck at libgnome-keyring1.0-cil"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by Blerp on 2009-03-07
Hello,

I'm upgrading my Jaunty Jackalope install and now it's stuck for about a night at the following:

```
root@rjeggens-desktop:~# apt-get install libgnome-keyring1.0-cil
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libgnome-keyring1.0-cil
1 upgraded, 0 newly installed, 0 to remove and 57 not upgraded.
1 not fully installed or removed.
Need to get 0B/14.4kB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package libgnome-keyring1.0-cil.
(Reading database ... 175927 files and directories currently installed.)
Preparing to replace libgnome-keyring1.0-cil 1.0.0~svn.r87622-1 (using .../libgnome-keyring1.0-cil_1.0.0~svn.r87622-2_all.deb) ...
Removing libgnome-keyring1.0-cil from Mono

```


Yes.. I do know I'm only trying to install libgnome-keyring1.0-cil here, but that's what dpkg --configure -a told me to do, reinstall it. The result is the same, it gets stuck at exactly this point.

What can I do to solve this? I do wanna upgrade my packages, as quite a lot have issues :)

---

### Post by Blerp on 2009-03-07
Ok.. I fixed it.. well.. sorta..

It seems that some 'mono' process just sat there doing nothing. I killed it and now it's proceeding again. I'm a happy camper!

Now to teach my Konsole to accept 'control-C' again and kill the process, instead of showing '^C' ...

---

### Post by basec0m on 2009-03-10
Thanks buddy...

---

### Post by directhex on 2009-03-11
I've been totally unable to reproduce the scattered "mono doesn't do anything" reports I've heard, sadly

---

