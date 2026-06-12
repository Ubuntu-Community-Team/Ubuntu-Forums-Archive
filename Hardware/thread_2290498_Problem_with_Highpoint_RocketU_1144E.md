---
title: "Problem with Highpoint RocketU 1144E"
date: 2015-08-12
forum: Hardware
---

### Post by nesur on 2015-08-12
I got a Highpoint RocketU 1144E card with the intention of using my only PCIe 4x slot as wisely as possible: 2x eSATA plus 2 USB 3.0 ports. The USB ports work right away, but the eSATA ports need a driver. Now I see that the drivers that Highpoint provides are only for older kernel versions. Following [this guide]("https://help.ubuntu.com/community/RocketRaid") and [this thread]("http://ubuntuforums.org/showthread.php?t=2214489") I modified the source to build [the driver]("http://www.highpoint-tech.com/USA_new/series_RocketU1144E_download.htm") in Ubuntu 14.04.

I changed what I thought I had to change following my instinct and the changes made in those other drivers, and I was able to compile and install the driver. I am attaching the patch to this message: [ATTACH]263799[/ATTACH]

Right after "make" I ran "make install" and it said it was replacing a previous driver, which made me worried (what, what that included in the stock kernel?). But I moved ahead and after "modprobe ru1144e" it actually worked! I had some errors in "dmesg" but it worked, I was able to connect to an external hard drive and access it.

After a reboot it stopped working, it just waits forever after "modprobe ru1144e" and I can't see the external hard drive. Any ideas what could be wrong? Needless to say, I rebooted, I recompiled and reinstalled the module, and reinstalled the kernel plus headers and rebuilt and reinstalled the module to no avail.

Maybe I did something wrong in my patch? I'm specially worried about the part that replaced
```

proc_info:               hpt_proc_info26,

```
with 
```

show_info:               hpt_proc_get_info,
write_info:              hpt_proc_set_info,

```

I wonder if somehow I'm not getting an error message because of this change. Any thoughts?

---

### Post by nesur on 2015-08-12
As an update, I noticed that when I run "sudo modprobe ru1144e" dmesg shows
```
[ 3895.869192] ru1144e:RocketU 1144E controller driver v1.0 (Aug 12 2015 17:22:59)
[ 3896.911449] ru1144e:adapter at PCI 4:0:0, IRQ 30
[ 3896.911477] ru1144e:adapter at PCI 5:0:0, IRQ 30
```
and when I'm tired of waiting for modprobe to come back, when I interrupt it shows
```
[ 4133.124300] ru1144e:init interrupted
```

Now interestingly, if I run "sudo modprobe -f ru1144e" I get the following error:
```
modprobe: ERROR: could not insert 'ru1144e': Exec format error
```

Just to make sure I did a "make clean" and then "make ARCH=x86_64" and "make install" but still no luck.

---

