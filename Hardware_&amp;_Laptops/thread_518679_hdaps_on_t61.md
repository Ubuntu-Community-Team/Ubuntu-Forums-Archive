---
title: "hdaps on t61"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by yohan on 2007-08-06
Ive been trying to get hdaps to work on my thinkpad t61 for a long time now. I've followed this guide:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Active_Protection_System_.28acceleration_monitor.29](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Active_Protection_System_.28acceleration_monitor.29)

With the latest kernel 2.6.22.1 with the patch:
# Latest sata/ide disk protection patch for 2.6.20,2.6.21 and 2.6.22 (new design)
from 
 [http://www.thinkwiki.org/wiki/HDAPS#Disk_head_parking](http://www.thinkwiki.org/wiki/HDAPS#Disk_head_parking)

After its all compiled and i reboot, i dont get anything when i do dmesg | grep hdaps
And if I do modprobe hdaps I get the same as with my regular kernel:
FATAL: Error inserting hdaps (/lib/modules/2.6.20-16-generic/kernel/drivers/hwmon/hdaps.ko): No such device

What am I doing wrong? 

I get the same if I install this kernel:
[http://axiomatization.googlepages.com/ubuntufeistydebpackagesforthinkpads](http://axiomatization.googlepages.com/ubuntufeistydebpackagesforthinkpads)

Thanks

---

### Post by yohan on 2007-08-06
bump.

Is there any special thing I have to activate in the kernel config?

---

### Post by smbm on 2007-08-06
I've managed to get it working under Gutsy. There's an HDAPS package in the repos but it didn't work so I just built it from the source using the guide on Thinkwiki and it works fine.

Good luck.

---

### Post by yohan on 2007-08-06
HDAPS package? You mean the hdapsd package, which you can also compile?

I can't even get the kernel driver to work, using the protection patch. Didn't you even recompile the kernel? does hdaps-gl work? (Its in the package hdaps-utils)

---

### Post by smbm on 2007-08-07
Sorry yeah it was HDAPSD from the repos. I didn't have to recompile the kernel, just the new module, then I modprobed it and it's working fine. hdaps-gl etc are working fine too.

---

### Post by yohan on 2007-08-07
yeah i install tp-smapi and now its working fine. thanks.

---

### Post by computx on 2007-10-27
Its late and I am probably being dense but the latest hdapsd source that I see is an attachment on a gmane discussion. I downloaded that as 1045-001.bin , renamed it to hdapsd.c
but when I try to compile with gcc -o hdapsd hdapsd-*.c
I get an error about no such file. 
When i try gcc -o hdapsd hdapsd.c I get multiple incompatible declaration errors.
Am I using the wrong source files or the wrong syntax or what?
Any help appreciated
Edit: finally got a newer verdion of hdapsd installed but it I am unable to protect the drive with 
echo 1 > /sys/block/sda/queue/protect
Is there a new wrinkle to protecting the drives with the new hdapsd?
btw I did not patch my kernel.

---

### Post by holihue on 2007-10-31
I can't compile tp-smapi from source.

```
$make load
Makefile:25: *** This driver requires kernel 2.6.19 or newer, and matching kernel sources. You may need to set KSRC and KBUILD to find these..  Stop.

```

What is wrong?


I had to use the Installation on Ubuntu/Debian...

But it works now... :):):):):):)





...Why is the sensor inverted?

---

### Post by rajbarua on 2007-11-20
> **smbm said:**
> Sorry yeah it was HDAPSD from the repos. I didn't have to recompile the kernel, just the new module, then I modprobed it and it's working fine. hdaps-gl etc are working fine too.
Hi,

I have been trying to get hard disk protection work but couldn't do it without a kernel rebuild. Kernel rebuild itself has led to a lot of problems with drivers etc so please could you tell how you managed to get it working without a custom kernel build.
If I just install tp_smapi and hdaps and hdaps-utils and start hdapsd I get the error:

```

/etc/init.d/hdapsd start
 * Not starting hdapsd: /sys/block/sda/queue/protect does not exist
```

Is it at all possible to  get hdaps working without building a custom kernel?

Thanks

---

### Post by bomanizer on 2008-01-27
> **rajbarua said:**
> Hi,

I have been trying to get hard disk protection work but couldn't do it without a kernel rebuild. Kernel rebuild itself has led to a lot of problems with drivers etc so please could you tell how you managed to get it working without a custom kernel build.
If I just install tp_smapi and hdaps and hdaps-utils and start hdapsd I get the error:

```

/etc/init.d/hdapsd start
 * Not starting hdapsd: /sys/block/sda/queue/protect does not exist
```

Is it at all possible to  get hdaps working without building a custom kernel?

Thanks

Bump, I'm stuck at here too... :(

---

### Post by ignoto on 2008-02-16
same problem here, recompiling hdaps.c and adding:

HDAPS_DMI_MATCH_INVERT("LENOVO", "ThinkPad T61"),

the kernel recognizes it:
```
root@ignoto-laptop:/mnt/D/HDAPS# dmesg | grep hdaps
[ 6322.320000] hdaps: inverting axis readings.
[ 6322.320000] hdaps: LENOVO ThinkPad T61 detected.
[ 6322.320000] input: hdaps as /class/input/input17
[ 6322.320000] hdaps: driver successfully loaded.
root@ignoto-laptop:/mnt/D/HDAPS#
```

but hdaps doesn't work already:
```
/etc/init.d/hdapsd start
 * Not starting hdapsd: /sys/block/sda/queue/protect does not exist
```

---

### Post by darrensnospam on 2008-04-24
Anything new on this one? I'd like to get active disk protection working as well.

---

