---
title: "nvagp driver won't load"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by DanP on 2005-04-09
Hi all,
(warning new user alert)
I just installed ubuntu (Hoary 2.6.10-5-amd64)and the nvidia drivers
from the repository and now I want to try the nvagp driver, however
the agpgart drivers load automatically at boot.

from dmesg:
agpgart: Detected AGP bridge 0
agpgart: Setting up Nforce3 AGP.
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xe0000000


And from /var/log/messages:
NVRM: not using NVAGP, an AGPGART backend is loaded!


How do I deactivate agpgart loading so that the nvagp drivers will load instead?

I've searched google and here for this info and all I found was a reference
to blacklisting the module, however the post didn't go into how to do this.

Any help would be appreciated, even just a reference to the proper documentation
or configuration file would help greatly. 

Also, thanks to all of the people who have contributed to make this a great O/S.

TIA,
Dan P

Gigabyte GA-K8NS
AMD64 3000+ 512mb
nvidia 5200

---

### Post by p!=f on 2005-04-09
[QUOTE=DanP]Hi all,
(warning new user alert)
I just installed ubuntu (Hoary 2.6.10-5-amd64)and the nvidia drivers
from the repository and now I want to try the nvagp driver, however
the agpgart drivers load automatically at boot.

from dmesg:
agpgart: Detected AGP bridge 0
agpgart: Setting up Nforce3 AGP.
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xe0000000


And from /var/log/messages:
NVRM: not using NVAGP, an AGPGART backend is loaded!


How do I deactivate agpgart loading so that the nvagp drivers will load instead?

I've searched google and here for this info and all I found was a reference
to blacklisting the module, however the post didn't go into how to do this.

Any help would be appreciated, even just a reference to the proper documentation
or configuration file would help greatly. 

Also, thanks to all of the people who have contributed to make this a great O/S.

TIA,
Dan P

Gigabyte GA-K8NS
AMD64 3000+ 512mb
nvidia 5200[/QUOTE]
Welcome on the forums

searching these forums gave me this:
[http://ubuntuforums.org/showpost.php?p=86653&postcount=21](http://ubuntuforums.org/showpost.php?p=86653&postcount=21)
:)
Hope it helps.

Good times with Ubuntu.

---

### Post by DanP on 2005-04-09
Thanks for the reply,

I don't how I missed it,just new to the forums I guess.

I blacklisted agpgart and agpgart-amd64.
unfortunatly it didn't work for me, the agpgart driver still interferes.

A complete search of the system  shows:
(sudo find / -name *agpgart*)
/usr/include/linux/agpgart.h
/dev/agpgart
/dev/.udevdb/class@misc@agpgart
/sys/class/misc/agpgart
/sys/bus/pci/drivers/agpgart-amd64
/.dev/agpgart

(sudo find / -name *agp*)
/usr/share/man/man1/tagpending.1.gz
/usr/bin/tagpending
/usr/include/linux/agpgart.h
/usr/include/linux/agp_backend.h
/usr/include/i386-linux/asm/agp.h
/usr/include/asm/agp.h
/dev/agpgart
/dev/.udevdb/class@misc@agpgart
/lib/modules/2.6.10-5-amd64-generic/kernel/drivers/char/agp
/lib/modules/2.6.10-5-amd64-generic/kernel/drivers/char/agp/intel-mch-agp.ko
/proc/driver/nvidia/agp
/sys/class/misc/agpgart
/sys/bus/pci/drivers/agpgart-amd64
/.dev/agpgart

(sudo find / -name *amd-64*)
comes up blank.

(sudo / -name *nforce*)
/usr/share/doc/lm-sensors/doc/busses/i2c-nforce2
/lib/modules/2.6.10-5-amd64-generic/kernel/drivers/i2c/busses/i2c-nforce2.ko
/sys/module/i2c_nforce2


The only reference is in the include files, the rest look like device files.  Possibly it is compiled into the stock kernel or loaded as part of another driver, maybe the NFORCE3 chipset or the i2c module?

The nvidia nforce drivers may help, but I'm leary of those as they have trashed my system before.

I'll include my dmesg and lsmod output incase it helps you to help me.
Any suggestions where to start?

Thanks,
DanP


Gigabyte GA-K8NS(nforce3)
AMD64 3000+ 512mb
(barely overclocked and stable)
nvidia 5200

---

### Post by p!=f on 2005-04-09
Looking at your attached lsmod.txt I can't see agpgart module loaded. What's the error you get when you start the xserver now?

---

### Post by nad on 2005-04-09
By now we all know that NvAGP will not load with agpgart already loaded. I like the referenced suggestion to rename agpgart.ko to keep it from loading. It is easily reversible.

I have been doing kernel recompiles to exclude agpgart and make a loadable module of my framebuffer support so that I can remove it at will. This obviously does not survive a kernel upgrade. So I have to force versioning. I am on the cusp of installing multi-seat systems, but, as nicely as the nVidia cards and driver behave in a multi-card setup, if the driver and distro are going to be a problem, I will look for alternatives.

For your reference, here is a wrapper script from the XFree Local multi-user HOWTO to load the nv or nVidia drivers from a nonstandard location. It allows you to install the driver files in a separate directory so that they play nice with each other and can be cleanly uninstalled. Modify to your needs as necessary. Note the symlink to the X server executable.

#!/bin/bash
#########################################################
### /usr/X11R6/bin/XNV                                ###
### script to start XFree with different LIBRARY_PATH ###
### in order to use Nvidia GL libraries and           ###
### XFree GL libraries at the same time               ###
#########################################################
  
export LD_LIBRARY_PATH=/usr/X11R6/libNV
exec /usr/X11R6/bin/X0 $*

# end code

Dan M

---

### Post by Astrophobos on 2005-04-11
Hi,

I have a similar problem. lsmod don't show agpgart module, but logs clearly show it !

lsmod | egrep -i "agp|nvidia|via"
```
nvidia               4569404  12
snd_via82xx            29856  0
snd_ac97_codec         80992  1 snd_via82xx
snd_pcm               102348  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
gameport                4992  1 snd_via82xx
snd_mpu401_uart         8192  1 snd_via82xx
snd                    58600  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
i2c_viapro              8652  0
via_velocity           35296  0
crc_ccitt               2496  1 via_velocity
i2c_core               24664  4 i2c_viapro,tda9887,tuner,saa7134
via82cxxx              14320  1
ide_core              150276  4 ide_generic,ide_disk,ide_cd,via82cxxx
sata_via                9476  10
libata                 55560  1 sata_via
```

cat /var/log/message | grep -i agp
```
Apr 11 08:28:59 localhost kernel: agpgart: Detected AGP bridge 0
Apr 11 08:28:59 localhost kernel: agpgart: Maximum main memory to use for agp memory: 941M
Apr 11 08:28:59 localhost kernel: agpgart: AGP aperture is 256M @ 0xe0000000
Apr 11 08:28:59 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Apr 11 08:29:02 localhost kernel: NVRM: not using NVAGP, an AGPGART backend is loaded!
```

trying sudo rmmod agpgart
```
ERROR: Module agpgart does not exist in /proc/modules
```

blacklisting it don't help either.

---

### Post by DanP on 2005-04-11
Sorry for the slow reply--I've been out of town for the weekend.

Yes, that is the problem. No AGPGART module loaded according to lsmod, yet a grep for "NVAGP" of the dmesg.txt I uploaded shows the conflict.
I don't have an agpgart module. According to a search of /lib/modules/ it doesn't exist at all.

My XOrg.log file doesn't show the conflict, it simply echos the ' "nvagp" "1" ' option from the xorg.conf file.

A search of my running kernel config shows a GART (GART-IOMMU) built into the kernel (not a module). I wonder if this is the culprit?  This is a stock kernel version: 2.6.10-5-amd64-generic.


Thanks for all your help,

Dan P.

---

### Post by Astrophobos on 2005-04-11
Don't know if it's relevant:

cat ~/linux/linux-source-2.6.10-2.6.10/debian/config/amd64/amd64-generic | grep -i agp
```
CONFIG_AGP=y
CONFIG_AGP_AMD64=y
CONFIG_AGP_INTEL_MCH=m
```

cat ~/linux/linux-source-2.6.10-2.6.10/debian/config/i386/386 | grep -i agp
```
CONFIG_AGP=m
CONFIG_AGP_ALI=m
CONFIG_AGP_ATI=m
CONFIG_AGP_AMD=m
CONFIG_AGP_AMD64=m
CONFIG_AGP_INTEL=m
CONFIG_AGP_INTEL_MCH=m
CONFIG_AGP_NVIDIA=m
CONFIG_AGP_SIS=m
CONFIG_AGP_SWORKS=m
CONFIG_AGP_VIA=m
CONFIG_AGP_EFFICEON=m
```

So it's seem AGP is builtin in AMD64 but as module in i386. I really don't know why, maybe somebody else can help?

---

### Post by DanP on 2005-04-12
I had a look at reconfiguring the kernel using the 2.6.11 sources
to build the driver as a module, however using "make xconfig" I was
 not able to change the setting for the apgart module.

It was not even listed until I enabled the show all options and at that
point the option was greyed-out and unchangable in the compiled in
state.  There was also a note to the effect that it was using the agp
(agpgart?) built into the amd64 processor (part of the memory controller?).
This may be why it is, as mentioned, built into the amd64 kernel and
not the 386 kernel.

I installed linux-kernel-2.6.11 to see if this has been changed in a newer
kernel version with no luck--still not listed with lsmod and the same conflict
showing in dmesg.

I'm still open to any suggestions, but I've gone about as far as I can go
until I educate myself enough on kernel options and building to try a
custom kernel for my hardware.

Thank you for all of the helpful input on this,

Dan P.

---

### Post by terrax on 2006-02-02
I have that exact same problem as you. I did solve it in gentoo, though I did find it easier there.

The reason it is loading agpgart, is that in the amd64 version, the IOMMU support in the kernel has to have the agpgart compiled in the kernel. If you want to completely remove the agpgart from loading, you have to recompile a new kernel without IOMMU and agpgart support. The IOMMU is only needed if you have over 4 gb memory installed :)

The agpgart is probably installed as a module in x86, because IOMMU is not used here, and agpgart can easily be removed from the kernel modules with a recompile. BUT? Here comes my problem. I have installer the x86 version on a amd64, and I really don't know where to start, recompiling a new kernel in this automated dist :S In gentoo it was rather easy, but in kubuntu you have to have some kernel-headers i think. Can anybody help me setting my system up, so I can recompile me kernel?

---

### Post by cfaulkner on 2006-10-11
I know this thread is sorta old, but i ran into the same problem and then i thought.  

Reload the nvidia drivers.. after disabling IOMMU in the Kernel and recompiling.  so i did.  and agpgart no longer shows up.  agpgart was disabled in the kernel, but the nvidia drivers thought it was still there, so a recompile of the nvidia drivers fixed the trick..

---

