---
title: "rt2860 driver in kernel 2.6.33"
date: 2010-02-25
forum: Hardware
---

### Post by nigelmouse on 2010-02-25
Hi,

I'm trying to run a newer kernel which provides a bug fix which effects my graphics card. I've tried installing 2.6.32-9 and 2.6.33 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and the kernel installs fine.

The issue I've got is while the newer kernel bug fix corrects the intended issue, it also appears to lose support for my wireless card. I'm using an eee901 laptop which under the latest karmic kernel (2.6.31-19) and that uses the rt2860 driver. This driver does not appear to exist in the modules/drivers directory of the newer kernels.

Is there something I have to do to enable support for my wireless card under newer kernels?

---

### Post by aLiEnTxC on 2010-03-05
I think this driver is not included in official kernel.

U have to use the driver from ralink 

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Greetings

---

### Post by roolebo on 2010-03-08
There are some changes with driver for rt2860. The previous one before kernel 2.6.33 was in staging tree and it was called rt2860sta. But now it was replaced by rt2800pci driver. I suggest the last has incorrect loading order. The problem is discovered in the official forum of the driver: [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?p=34014&sid=ec979d18bd7626ca3a9661e236b9caf4#p34014](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?p=34014&sid=ec979d18bd7626ca3a9661e236b9caf4#p34014)

---

### Post by andreab on 2010-03-27
you can have a look here:
[http://ubuntuforums.org/showthread.php?t=1045703](http://ubuntuforums.org/showthread.php?t=1045703)

I did it and works

---

### Post by meijer.o on 2010-03-27
Dear linux user,

I have an eeepc 1000h that needs the rt2860sta module. The 2.6.33 kernel from the ppa has been compiled without this staging module, so your wifi card will not work. I compiled the 2.6.33 kernel myself for this reason. The staging module of this kernel works fine.

Kind regards,

Otto Meijer

---

