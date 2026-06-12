---
title: "Cant install nic driver, dont understand why."
date: 2009-02-16
forum: Hardware
---

### Post by RedG on 2009-02-16
Hi all!

I run Ubuntu 8.10 64-bit on a custom kernel (2.6.28.4).
When I compiled the kernel and the modules, I think I choosed the wrong driver for my nic. (I unmarked all other nic's, and everything else I thought didn't need). Everything running smoothly except for the wrong driver for my nic. After Googeling my nic "NetXtreme BCM5788 Gigabit Ethernet" I think I should have used tg3.ko (Tigon3). 
I followed this post to compile just the one driver I needed. 
[http://ubuntuforums.org/showthread.php?t=1012054](http://ubuntuforums.org/showthread.php?t=1012054)

Everything seems to go fine until it's time to run ```
sudo modprobe tg3
```
then I get FATAL: Module tg3 not found.
I have copied tg3.ko from my folder to the /lib/modules/2.6.28.4/kernel/drivers/net (I used "locate tg3.ko" and put it in the same folder as the other tg3.ko for the other kernels)

OK, I could recompile my kernel and/or all the modules - but then I wouldn't learn how to do this. And it ain't that fun to recompile, done that, been there.

The strange thing is that when I have put the file in, what I believe is the correct, folder and use "locate tg3.ko" only the tg3.ko files for the "old" kernels show up. If I run "locate tg3", I get the tg3.ko files for the other kernels and the tg3.h and tg3.c in the source dir /usr/src/linux-2.6.28.4/drivers/net.

If I use Nautilus or the terminal I can confirm that there is a file named tg3.ko in the /lib/modules/2.6.28.4/kernel/drivers/net dir.

In terminal, when in /lib/modules/2.6.28.4/kernel/drivers/net, and I use modinfo tg3.ko I get answer that, in my eyes, looks OK.

What am I missing??

Why cant I install my new driver?

Thanks in advance
RedG

---

### Post by RedG on 2009-02-17
I answer my self.
I found this page, using Google once again.
[http://www.captain.at/programming/kernel-2.6/](http://www.captain.at/programming/kernel-2.6/)

The Makefile looks a little different from the one I used in my first post, but is in essence the same.
But here the writer use an install script, so I copied the script and made the necessary changes - and volá, it worked!!! :D

For those who are interested here is what the script looked like

Install.sh
```
#!/bin/bash
install -m 644 tg3.ko /lib/modules/`uname -r`/kernel/drivers/net/tg3.ko
/sbin/depmod -a

```
Just remember to make the script executable, I didn't on my first try.

---

