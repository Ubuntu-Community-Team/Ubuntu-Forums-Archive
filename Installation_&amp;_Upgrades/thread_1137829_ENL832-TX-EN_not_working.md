---
title: "ENL832-TX-EN not working"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Dagahk on 2009-04-25
Hello.

I've been using Ubuntu for a long time now, since 2005 versions. Been in love with it, really like it.

Well, I got a problem with 9.04 Ubuntu i386 on a computer, because its PCI device for Network is Enl832-tx-en, and the kernel do not have the driver needed.

When I type $sudo lshw -C network, it says the device is UNCLAIMED, meaning there is really no driver installed for this.

So, I googled it and found on the official site a driver, surprisingly, for Linux as well. But when I try to install it, there are a lot of problems on command '$make all' because the driver was made for an older Kernel version.

So, I can't install from the driver that official site gives.

Any suggestions? Fixes?

Thanks in advance!

EDIT: After many days searching and hours cracking my head, I finally solved it. It seems that 9.04 build comes with Sundance Module already activated, but that module cannot recognize for some reason the network. It wasn't necessary recompile and replace. I found out that simply typing

rmmod sundance
modprobe sundance

meaning, remove the mod and execute the mod, makes the hardware recognizable. So I added both lines in /etc/rc.local.

That's it, thanks.

---

