---
title: "FATAL: Module binfmt_misc not found."
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by shateredsoul on 2009-03-01
So I really messed up my machine.. at first the usb drives wouldn't work. So I restarted it.. now it gets stuck on the load up screen with the following info.

*Enabling additional executable binary formats binfmt-support
FATAL: Module binfmt_misc not found.
update-finfmts: warning: Couldn't load the minfmt_misc module.

*Checking battery state...
/dev/sda
setting Advanced Power Management level to 0xfe (254)

and that's all i see (plus some other stuff that started up before that)

Is there anyway to undo what I did?

this is what I did to mess my up my ubuntu :

> 
chmod 644 usbcore.ko
sudo cp usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot

I downloaded a file called usbcore.ko from [http://www.scott-wallace.net/misc/us...072-mod.tar.gz](http://www.scott-wallace.net/misc/us...072-mod.tar.gz)

It restarted, the usb drives stopped working. I tried "sudo depmod +ae" for some reason.. to see if I could undo what i did and it said something along the lines of "no such command". I then restarted my machine and received the screen I described (all black, only white text)

I tried turning my computer off and on.. nothing.

before restarting I ran dmesg |tail -n 20

this is what I received

[ 18.807523] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 19.457777] ACPI: WMI: Mapper loaded
[ 20.511358] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[ 20.586370] apm: BIOS not found.
[ 20.792407] ppdev: user-space parallel port driver
[ 24.308095] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 24.308107] vboxdrv: Successfully done.
[ 24.308112] vboxdrv: Found 1 processor cores.
[ 24.310940] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[ 24.310951] vboxdrv: Successfully loaded version 2.1.2 (interface 0x000a0009).
[ 30.627402] [drm] Initialized drm 1.1.0 20060810
[ 30.632783] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 30.632791] pci 0000:00:02.0: setting latency timer to 64
[ 30.633848] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 30.697317] NET: Registered protocol family 17
[ 58.440927] ieee80211_crypt: registered algorithm 'WEP'
[ 64.381049] NET: Registered protocol family 10
[ 64.382647] lo: Disabled Privacy Extensions
[ 64.384422] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 74.492026] eth1: no IPv6 routers present

---

