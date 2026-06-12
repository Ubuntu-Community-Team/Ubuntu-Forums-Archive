---
title: "Can't get DMA to work"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by ry_ry on 2005-09-02
Hi, I can't seem to get DMA on any of my drives.
I'm using the 32bit version of Ubuntu 5.04 and here are my PC specs:
emachines W3410
AMD64 3200+
512MB DDR 400
80GB Samsung HD
ATI Xpress 200 with an open PCI express slot
DVD+/-RW drive

The motherboard is a MSI 7145 RS480M using the ATI chipset.
I've tried everything I could find.
1. tried amd74xx in /etc/modules "doesn't work"
2. tried atiixp in /etc/modules "doesn't work"
3. tried commenting out the ide stuff in /etc/modules and using either one of amd74xx or atiixp "doesn't work"
4. tried inserting amd74xx or atiixp in both /etc/modules and /etc/hotplug/blacklist "doesn't work"
5. tried sudo hdparm -d1 /dev/hda under the above conditions "doesn't work"
6. tried compiling a custom kernel of 2.6.10 in order to turn on DMA in the kernel using the Kernel Compilation for Newbies guide posted in this forum "doesn't work" no change in transfer speeds.

hdparm -i /dev/hda tells me the drive is using udma5.
hdparm -tT /dev/hda tells me this:
Timing cached reads: 2652 MB in 2.00 seconds = 1324.22 MB/sec
Timing buffered disk reads: 4 MB in 3.74 seconds = 1.07 MB/sec

I always get a Operation not permitted error whenever I tried to enable DMA either on the hard drive or the DVD burner.

Ubuntu runs slower than my grandma on this system and it seems to be because DMA is not enabled. Is there anyway to enable DMA using the 2.6.10 kernel?

I heard that the 2.6.11 kernel has DMA working for my system, but since this is not an official Ubuntu kernel I would rather not use it.

Anybody know whats wrong and how to fix it? This DMA thing is driving me crazy.  ](*,)

---

### Post by Perfect Storm on 2005-09-02
Have you tried this? [http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)
Just make sure to use the right input for devices etc.

---

### Post by ry_ry on 2005-09-02
[QUOTE=Artificial Intelligence]Have you tried this? [http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)
Just make sure to use the right input for devices etc.[/QUOTE]

yes, I tried the sudo hdparm -d1  for both the hard drive /dev/hda/ and the DVD burner. I tried /dev/hdc.../dev/cdrom.../dev/dvd also and none of my drives will let me enable DMA. Even the hard drive won't let me enable DMA.

---

### Post by kybKenny on 2006-11-15
Same problem here after Upgrade from Dapper to Edgy.

I'm using a nx6125 notebook from HP.

Unfortunately, i don't have a solution yet, but i'm trying a custom 2.6.18.1 kernel right now.

Will let you know if it worked, though i am not very hopeful, regarding your post about this.

Regards

Kenny

---

### Post by kybKenny on 2006-11-17
Ok, after forgetting to enable the initrd (big mistake :-) )

(this can be easily fixed using this:) ```
update-initramfs -k 'the_version_of_your_new_kernel' -c
```

i do have now a 2.6.18.1-kernel running, with DMA enabled.
And see, it works.

Unfortunately, there is no Ndiswrapper module here... would i have had to apply a patch to the kernel.org sources?

```
dorian@znuznu:~$ grep -i ndiswrapper /boot/config-2.6.17-10-generic 
CONFIG_NDISWRAPPER=m
dorian@znuznu:~$ grep -i ndiswrapper /boot/config-2.6.18.1 
dorian@znuznu:~$ 

``` 

And second issue is, i can't see the booting process (not that it's so fast, it's just a black screen until log-in to X)
Did i mess up the Framebuffer set-up?

the diff in config regarding fb between the 2.6.17-10-generic and my 2.6.18.1:

```

7c7
< CONFIG_FB_FIRMWARE_EDID=y
---
> # CONFIG_FB_BACKLIGHT is not set
10,13c10,12
< CONFIG_FB_CIRRUS=m
< CONFIG_FB_PM2=m
< CONFIG_FB_PM2_FIFO_DISCONNECT=y
< CONFIG_FB_CYBER2000=m
---
> # CONFIG_FB_CIRRUS is not set
> # CONFIG_FB_PM2 is not set
> # CONFIG_FB_CYBER2000 is not set
18,63c17,37
< CONFIG_FB_VESA=m
< CONFIG_FB_HGA=m
< # CONFIG_FB_HGA_ACCEL is not set
< CONFIG_FB_S1D13XXX=m
< CONFIG_FB_NVIDIA=m
< CONFIG_FB_NVIDIA_I2C=y
< CONFIG_FB_RIVA=m
< CONFIG_FB_RIVA_I2C=y
< # CONFIG_FB_RIVA_DEBUG is not set
< CONFIG_FB_I810=m
< # CONFIG_FB_I810_GTF is not set
< CONFIG_FB_INTEL=m
< # CONFIG_FB_INTEL_DEBUG is not set
< CONFIG_FB_MATROX=m
< CONFIG_FB_MATROX_MILLENIUM=y
< CONFIG_FB_MATROX_MYSTIQUE=y
< CONFIG_FB_MATROX_G=y
< CONFIG_FB_MATROX_I2C=m
< CONFIG_FB_MATROX_MAVEN=m
< CONFIG_FB_MATROX_MULTIHEAD=y
< CONFIG_FB_RADEON=m
< CONFIG_FB_RADEON_I2C=y
< # CONFIG_FB_RADEON_DEBUG is not set
< CONFIG_FB_ATY128=m
< CONFIG_FB_ATY=m
< CONFIG_FB_ATY_CT=y
< CONFIG_FB_ATY_GENERIC_LCD=y
< CONFIG_FB_ATY_GX=y
< CONFIG_FB_SAVAGE=m
< CONFIG_FB_SAVAGE_I2C=y
< CONFIG_FB_SAVAGE_ACCEL=y
< CONFIG_FB_SIS=m
< CONFIG_FB_SIS_300=y
< CONFIG_FB_SIS_315=y
< CONFIG_FB_NEOMAGIC=m
< CONFIG_FB_KYRO=m
< CONFIG_FB_3DFX=m
< # CONFIG_FB_3DFX_ACCEL is not set
< CONFIG_FB_VOODOO1=m
< CONFIG_FB_CYBLA=m
< CONFIG_FB_TRIDENT=m
< # CONFIG_FB_TRIDENT_ACCEL is not set
< CONFIG_FB_GEODE=y
< CONFIG_FB_GEODE_GX=m
< CONFIG_FB_GEODE_GX1=m
< CONFIG_FB_IMAC=y
---
> CONFIG_FB_VESA=y
> # CONFIG_FB_IMAC is not set
> # CONFIG_FB_HGA is not set
> # CONFIG_FB_S1D13XXX is not set
> # CONFIG_FB_NVIDIA is not set
> # CONFIG_FB_RIVA is not set
> # CONFIG_FB_I810 is not set
> # CONFIG_FB_INTEL is not set
> # CONFIG_FB_MATROX is not set
> # CONFIG_FB_RADEON is not set
> # CONFIG_FB_ATY128 is not set
> # CONFIG_FB_ATY is not set
> # CONFIG_FB_SAVAGE is not set
> # CONFIG_FB_SIS is not set
> # CONFIG_FB_NEOMAGIC is not set
> # CONFIG_FB_KYRO is not set
> # CONFIG_FB_3DFX is not set
> # CONFIG_FB_VOODOO1 is not set
> # CONFIG_FB_CYBLA is not set
> # CONFIG_FB_TRIDENT is not set
> # CONFIG_FB_GEODE is not set

```

regarding these patches and stuff, is there a place anyways where i can find the patches that got applied to the ubuntu-kernels?

I'm attaching my .config (unfortunately, you can't upload files without .something behind them... so it's a .zip)

As we're talking about a notebook, this could be optimised along the way, as we don't have too much different hardware in our computers :D 

[ATTACH]19525[/ATTACH]

---

