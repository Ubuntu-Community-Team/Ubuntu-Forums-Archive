---
title: "Dell Optiplex 740 and DVD player lost of material recognition"
date: 2009-08-14
forum: Hardware
---

### Post by totoroavi on 2009-08-14
Hi everyone,
At my office we have many Dell Optiplex 740 where we want to install kubuntu (jaunty in first and after the karmin). We can install in most of time, but for some material configuration we have a DVD player problem.
It's impossible to install, the PC boot but after when we try to install the kerne look to lose ths DVD player and after few moment we arrive in a shell.

I try a installation in Hardy and it's work well. It's look to be a kernel problem. If the kernel is up than 2.6.24 it's impossible to install (so we can't install on Intrepid and Jaunty.

I found some bug report on it in the launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/344093]("https://bugs.launchpad.net/ubuntu/+bug/344093")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344128]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344128")

Has you can see 2 to 3 DVD player make problem. So I don't think the problem come frome them, I think more fore a motherboard shipset or something like that.

Here you can found the information about our testing PC:
the lshw:
[http://pastebin.com/f39a0cac7]("http://pastebin.com/f39a0cac7")
the lspci:
[http://pastebin.com/f490ff56b]("http://pastebin.com/f490ff56b")
the lsusb:
[http://pastebin.com/f4ceff3a5]("http://pastebin.com/f4ceff3a5")
the dmesg under a 2.6.24 kernel:
[http://pastebin.com/f39cbbcea]("http://pastebin.com/f39cbbcea")
the dmesg under a 2.6.28 kernel:
[http://pastebin.com/f1a7fa10d]("http://pastebin.com/f1a7fa10d")

If the DVD player works, we're going to clone the PC. So don't be afraid to say we have to add a module to the kernel or something like it.

Any idear to correct this will be grate, in the frensh forum we try to add all_generic_ide at the and of the kernel boot option and to try to found a bios configuration (make the Sata look like IDE) but our bios don't have this option (I try with 3 different type of bios with the last one).

Thank's a lot for your help

totoro

---

