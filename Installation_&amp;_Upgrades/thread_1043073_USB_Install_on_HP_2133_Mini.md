---
title: "USB Install on HP 2133 Mini"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by firebadger on 2009-01-18
I'm trying to install Kubuntu on a HP2133 and I'm slowly being driven mad.

It doesn't have a CD drive so I had to create a bootable USB stick instead. I did this using Unetbootin diskimage (instructions [here]("http://tombuntu.com/index.php/2008/08/27/create-a-bootable-usb-drive-or-memory-card/")).

I tried the normal kubuntu install iso but it froze after a while and I understand that I need to set the kernel options *live xforcevesa* but I couldn't figure out how to do that successfully with my Unetbootin usb boot disk. Has anybody any advice on this?

I then tried the alternate CD which by default (in my case anyway) seems to use a command line installer. This runs all the way though, but left things with a invalid partition table. I tried this twice - just in case - but it happened both times.

If anybody has any thoughts, tips or ideally a step by step guide to installing *Kubuntu* 8.10 on the HP2133 that doesn't require me to have a Windows machine or Windows already installed on it I'd be very grateful.

---

### Post by firebadger on 2009-01-18
I tried the normal install iso again and edited the syslinux.cfg file on the USB stick to add in the xforcevesa option but still no joy. My syslinux.cfg file looks like this..

```

default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/kubuntu.seed boot=casper xforcevesa quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit

label ubnentry1
menu label oem=OEM install (for manufacturers)
kernel /ubnkern
append initrd=/ubninit oem=oem-config/enable=true

```

Again, any ideas gratefully received.

---

