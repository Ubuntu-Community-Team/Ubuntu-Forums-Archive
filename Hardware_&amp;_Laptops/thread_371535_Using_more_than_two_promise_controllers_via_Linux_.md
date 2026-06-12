---
title: "Using more than two promise controllers via Linux Kernel Module"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by Pontifex on 2007-02-27
I'm trying to put together a file server with all my antiquated IDE hard drives to store my volatile data on.  In the past with previous file server efforts I've been able to use as many as 5 or 6 hard drives for archiving data.  I've done this through those wonderful mainstays of hard drive controllership, Promise controllers.

I love these things.  I liked them so much I bought two new ones (ultra133 tx2) to go with my older models; ultra100 and a ultra133 I purchased previously, total of 4.  When putting them in my system and hooking up my hard drives I was shocked to discover that more than two of the same controller (ultra133 tx2) would negate the detection of hard drives attached to any of the controllers.  I asked Promise about the problem and the responded that they don't officially support more than one controller per computer; In broken engrish.

I checked that the module for the controllers was properly inserted and hoped that Ubuntu would take care of the problem:

```

lsmod
Module                  Size  Used by
binfmt_misc            10888  1
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
<snip>
pdc202xx_new            8192  2
forcedeth              19072  0
ehci_hcd               29448  0
ohci_hcd               18564  0
<snip>
ide_core              125268  4 pdc202xx_new,ide_disk,ide_generic,amd74xx
unix                   24624  580
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

It didn't.  I plugged in a known good drive to all ports on the controllers with three of the four controllers inserted.  Ubuntu shows that there are no volumes available besides the boot drive.

I asked my good friend about a solution and he vaguely recalled a kernel module that would allow Linux (Ubuntu in this case) to boot the Promises' BIOS out of memory and take control of them; As much the same the OS in modern OS's kicks the antiquated system board BIOSes out of memory and controls the hardware with a HAL or work-alike.

Unfortunately my friend only knew how to “roll his own kernel” with this module installed in Gentoo.  I don't know the first thing about rolling a kernel in Ubuntu, as I come from the wonderful world of Gentoo myself and am only dabbling with your wonderful software.  I assume that the procedure is the same, but I worry about Ubuntu specific kernel options / optimizations and I wondered if there was an easier way to go about things rather than just running 'make menuconfig' and flailing away at it.

So my questions are:

1)Is there an easy way (without resorting to kernel mangling) that I can use to access drives on all four Promise controllers?

2)Is there a specific kernel module (name and heading) that I can enable to allow Ubuntu to manage my Promise controllers?  And if so, is there a way to insert the module into the kernel at run time without a recompile?

3)If there isn't a nice way to do this, is there a document(s) that outlines the steps needed to create my own kernel modifications and still not upset Ubuntu?

4)If there isn't a guide, is there documentation that details the way that the Ubuntu kernel is setup (specific options) so that I don't mess anything up when I go to modify the kernel?

--Pontifex

---

### Post by Pontifex on 2007-02-27
I found something detailing how to install a kernel!  Excellent.  Why it would be under install notes and not under its own section, I'll never know.

But here's the [link](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html).

This still doesn't answer my questions about the module described above and if there's a better way.

Please enlighten me.

--Pontifex

---

