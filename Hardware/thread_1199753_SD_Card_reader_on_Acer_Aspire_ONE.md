---
title: "SD Card reader on Acer Aspire ONE"
date: 2009-06-29
forum: Hardware
---

### Post by pmatos on 2009-06-29
Hi all,

After successfully installing ubuntu netbook remix 9.04 on the acer aspire one I was trying to configure the sd card reader following the few instructions on 
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

It says to add some lines to modprobe.d/aspireone and add pciehp to /etc/modules
However, this instruction seems to be for an old ubuntu installation and not for 9.04 because pciehp cannot be found. Any ideas on how to get the sd card reader on this one?

Cheers,

Paulo Matos

---

### Post by bacil on 2009-07-20
Hi, i had similar problem but found solution. after spending time on google and various forums and testing this and that found this solution.

```
sudo vi /etc/modprobe.d/options.conf
```

Note: options.conf instead of options since any module configuration will require .conf suffix in future relaeases

in to otions.conf file insert these lines

```

options sdhci debug_quirks=1
ProblemType: Bug
Architecture: i386
DistroRelease: Ubuntu 9.04
Package: linux-image-2.6.28-6-generic 2.6.28-6.17
ProcCmdLine: User Name=UUID=e309fb14-05db-4e9a-b137-c6bf63eeb6a4 ro quiet splash elevator=noop
ProcEnviron:
SHELL=/bin/bash
LANG=it_IT.UTF-8
ProcVersionSignature: Ubuntu 2.6.28-6.17-generic
SourcePackage: linux

```

this works since pciehp module is obsoleted in 9.04 and it is part of kernel. 

There is one more test i have done and it worked but it spits out some warnings during boot so it is not recomanded, but if you want to try let me know if that helps

```
vi /boot/grub/menu.lst
```

and in ther find your default boot line and add 

```
pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1
```

so your boot line shoud look like this

```
/boot/vmlinuz-2.6.28-13-generic root=UUID=5cc2086f-e6e8-4da9-99c3-ef9ab261d9a3 ro quiet splash pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1
```

hope this helps.

and BTW sometimes my right reader doesnt apear right away but just suspend and restore brings it to life. i hvent found any reason for this behaviour yet.

---

### Post by Neva on 2011-06-08
There are handy solutions for various versions of AspireOne and Ubuntu here:
[https://help.ubuntu.com/community/AspireOne/](https://help.ubuntu.com/community/AspireOne/)

As of writing this text, 10.04, 10.10 and 11.04 are included for example on AspireOne model ZG5
[]("https://help.ubuntu.com/community/AspireOne/")

---

