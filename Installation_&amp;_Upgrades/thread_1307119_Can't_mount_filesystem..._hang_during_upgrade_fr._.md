---
title: "Can't mount filesystem... hang during upgrade fr. 9.04 to 9.1 - HELP~"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by wcbenyip on 2009-10-30
Hi there~

While I am upgrading my ubuntu 9.04 to 9.1, I found that the screen saver cannot be activated... as I need to go out and don't want others to access to my PC in the upgrading process... so I tried to switch to init 1 by pressing CTL+ALT+1.... then the nightmare begins...!!

I found the console is totally hang... so my only way is to reboot it (on the next morning, as I want to let it be upgrading to see whether it can still work~) ... after the kernel return.... it's always saying that some of the filesystem can't be mounted... and even the root filesystem is readonly now... and found the data partition & the swap partition can't be mounted.... 

Everyone could urgently help or advise how should be checked / follow-up to fix this issue... or even how to re-upgrade the 9.1?? Many thanks in advance!! PLEASE HELP~~

:(

---

### Post by wbm on 2009-10-30
Almost the exact same thing happened to me too.
Started upgrade last night, came back to blank screen in the morning. Had to reboot with the power button and now file systems cannot be mounted.

---

### Post by wcbenyip on 2009-10-30
Oh..... 

Is it possible to use a boot CD with 9.1 to recover the issues?? :(

---

### Post by guy-rouillier on 2009-11-02
I think I may have encountered the same issue.  I'm using VirtualBox to run both a 32-bit and a 64-bit version of Ubuntu.  The 32-bit upgrade completed without issue.  The 64-bit issue ran overnight, and when I checked in the next morning, the upgrade was hung installing one of the packages.  I rebooted, and now it is telling me it is unable to mount the filesystems.

I'm just playing around with these Ubuntu VMs, so it is not worth my time to debug this.  If I want the 64-bit Ubuntu in the future, I'll just install it again from scratch.

---

