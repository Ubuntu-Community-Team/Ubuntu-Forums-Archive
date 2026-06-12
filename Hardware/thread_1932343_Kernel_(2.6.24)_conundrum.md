---
title: "Kernel (2.6.24) conundrum"
date: 2012-02-27
forum: Hardware
---

### Post by D0natell0 on 2012-02-27
Hi,
I'm attempting a hardware upgrade to a PC that's running Ubuntu 8.04  LTS. 

I've installed the 2.6.24-30 Linux kernel, but it seems there's a symbolic link missing under /lib.

The system I've got is a custom build PC (CPU - Intel Core 2 Duo P8600 2.4GHz, 2Gb RAM, 60Gb SSD).

The instructions supplied for installing the device driver specify  that the Linux kernel source needs to be available. I've built and installed the Linux kernel, but it looks like something's still missing (see attached screenshot).
 
 The command "ls -l /lib/modules/$(uname -r)/{build,source}" is supposed to return two symbolic links, but I'm only getting one. 
 
 I expect I've missed a step somewhere, so do you have any ideas what I'm missing?
 Any suggestions most appreciated ;)

---

### Post by gordintoronto on 2012-02-27
Life would be a lot simpler if you used the latest version.

---

### Post by D0natell0 on 2012-03-02
My solution was to manually add the missing symlink:

[HTML]>sudo ln -s /usr/src/linux-header-2.6.24-30-generic 
/lib/modules/2.6.24-30-generic/source
[/HTML]

Thanks.

---

