---
title: "apt-get fails on libxi-dev? Can't boot into X?"
date: 2008-11-02
forum: General Help
---

### Post by ashton88 on 2008-11-02
Summary:
- Can't boot into 2.6.27-7 because of D945 bug ([_here_]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/290153"))
- Booting into previous 2.6.24-21 no GUI - No driver
- Can't recompile Nvidia driver, might be because:
- apt-get fails on install of libxi-dev, maybe because:
- I think I'm accidentally on a test/unstable version now?

Top it all of with the fact that I'm a newb, and in way over my head - so if I can provide any file outputs to make this easier I'd be happy to, I just don't know where to start.  Maybe at the beginning:
   
After upgrading (using synaptic) from 8.04 to 8.10 I followed the instructions in the Ubuntu Intrepid guide [_here_]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid") and replaced the contents of my sources.list file.  I suspect this is one of my many mistakes and that this guide just hasn't been updated.

Ubuntu upgraded a bunch of packages, and now when I log in the terminal I see that I am on something called lenny/sid - which I am figuring is some kind of test/unstable version.

This might be why apt-get has this error on a package:
> dpkg: error processing /var/cache/apt/archives/libxi-dev_2%3a1.1.3-2build1_i386.deb (--unpack):

After reading around I suspect that this error has something to do with why when I run the script to compile my Nvidia driver so I can boot back into 2.6.24-21 it just stops - nothing happens after I hit "compile."  (but maybe that's a whole other problem).

The reason I am having to boot into an earlier version of the kernel is that I have the bug described [_here_]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/290153"), and the work arounds aren't working for me.

So I have spent the better part of 2 days obsessively working through this, making no progress (aside from my theories of what happened) but I am in way over my head, so any help would be great.  I really want to get back to a stable version of Ubuntu. And booting into X would be great.

Right now I only have Terminal access (no gui).

I will name my first born after anyone who can help ... if my wife says its OK. ;)

---

