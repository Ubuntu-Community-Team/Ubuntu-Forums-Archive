---
title: "boot kernel freeze because of BCM4313 (natty)"
date: 2011-06-01
forum: Hardware
---

### Post by codef on 2011-06-01
Hi,
 I've got a Samsung np-rf510 as well and Ubuntu Natty. It contains the wifi card  BCM4313. When I turn it off in BIOS Natty boots without any problems. When I turn it on, it hangs while booting.

I'm using kernel 3.0.0 ppa ([http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-06-01-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-06-01-oneiric/)) as someone said it would be better. The original natty kernel showed the same behaviour.
/usr/log/jockey says:
WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver

[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979) does not work, because /lib/modules/3.0.0-9999/build does not exists. However, 
the kernel headers are installed:
linux-headers-3.0.0-999-generic_3.0.0-999.201106010905_amd64.deb		linux-headers-3.0.0-999_3.0.0-999.201106010905_all.deb
linux-image-3.0.0-999-generic_3.0.0-999.201106010905_amd64.deb

Thanks
Marc

---

### Post by coffeecat on 2011-06-01
I see that you have installed the STA driver. This may have been a  mistake but I don't blame you because Jockey harrasses you (quite unnecessarily) to do so, and there is a lot of advice floating about the forum concerning Broadcom drivers, but from people who do not have direct experience of your particular Broadcom chipset.

I have the same BCM4313 card in my HP netbook and I can tell you it works just fine with the default brcm80211 driver (the new open source one) that comes in the box in Natty. That's with the 2.6.38 kernel too.

One caveat. I am using a 32-bit install with my HP. One thread I was involved in, the OP was unable to get their BCM4313 working in a 64-bit install. Somehow I doubt that the driver would work in a 32-bit system, but not in a 64-bit, but that  point remains unanswered.

Question. You say the system hangs while booting if the wi-fi is not turned off. Was that so with the live CD session before you installed? That is, without the STA driver installed? Try booting up with the live CD/USB and see whether booting works with the wi-fi enabled and whether wireless works with the in-the-box driver. If yes to both I wouldn't know how you would decontaminate your system from the STA driver (it may have spammed your blacklist.conf file), but at least that would give you something to go on.

---

### Post by codef on 2011-06-02
>I see that you have installed the STA driver. This may have been a mistake but I don't blame you because Jockey harrasses you (quite unnecessarily) to do so, 
>and there is a lot of advice floating about the forum concerning Broadcom drivers, but from people who do not have direct experience of your particular 
>Broadcom chipset.
 Alright. I see.

>I have the same BCM4313 card in my HP netbook and I can tell you it works just fine with the default brcm80211 driver (the new open source one) that comes in 
>the box in Natty. That's with the 2.6.38 kernel too.
 I've formatted the relevant partitions and installed Ubuntu Server Natty. iwlist wlan0 scan shows the available networks.

>One caveat. I am using a 32-bit install with my HP. One thread I was involved in, the OP was unable to get their BCM4313 working in a 64-bit install. Somehow >I doubt that the driver would work in a 32-bit system, but not in a 64-bit, but that point remains unanswered.

>Question. You say the system hangs while booting if the wi-fi is not turned off. 
 Nope, it the only way to get it works was to turn off wi-fi in BIOS.

>Was that so with the live CD session before you installed? That is, without the STA driver installed? Try booting up with the live CD/USB and see whether 
>booting works with the wi-fi enabled and whether wireless works with the in-the-box driver. If yes to both I wouldn't know how you would decontaminate your 
>system from the STA driver (it may have spammed your blacklist.conf file), but at least that would give you something to go on.
 Lubuntu LiveCD 32 bit crashed.
 I now tried Ubuntu Natty 32 bit live cd and it worked. Ubuntu Server x64 command line works as well.

Now it works (Ubuntu Server Natty + LXDE)! It seemed to be a problem with the nouveau drivers plus the BCM4313. When I use the NVidia restricted drivers, everything works. As you stated there is no reason to install the driver via jockey.

Thanks you very much for your help.

---

### Post by coffeecat on 2011-06-02
> **codef said:**
> It seemed to be a problem with the nouveau drivers plus the BCM4313. When I use the NVidia restricted drivers, everything works.

Thanks for the feedback. It's useful getting information like this from other users. My HP netbook uses Intel graphics so clearly I wasn't going to see this.

---

