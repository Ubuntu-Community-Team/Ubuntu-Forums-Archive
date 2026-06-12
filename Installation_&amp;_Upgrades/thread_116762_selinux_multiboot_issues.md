---
title: "selinux multiboot issues"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by savage on 2006-01-13
This is meant to be a simple warning; do some research before trying to multiboot with distros that use SELinux (Security Enhanced Linux). I wanted to install RHEL clone CentOS so that the small company I work for; in case of ROBAB (Run Over By  A Bus) scenario, could scale up to commercial support. Since most of my experience has been with Debian based distros I wanted to have Ubuntu on the computer as well, and since the hardware is 64bit I wanted to have a 64bit distro as well. Long story short, I tried many times and scoured many forums trying to troubleshoot the failing install. At first I was trying to share the /home directory, then only swap, I also tried setting SELinux to warn, and finally disabled. No matter what happened the installs failed, and even CentOS would crap out after a few boots. I don't know all the details but it appears that [SELinux doesn't play nice with others]("http://lwn.net/Articles/165530/").

The specific error I was receiving was:

VFS: Cannot open root device "hdb5" or unkown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)

---

