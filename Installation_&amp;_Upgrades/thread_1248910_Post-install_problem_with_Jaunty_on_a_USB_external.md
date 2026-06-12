---
title: "Post-install problem with Jaunty on a USB external hard drive"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by lfb on 2009-08-24
I have a 1Tb Western Digital USB external hard drive, which I am trying to install Ubuntu on.  In this attempt, I ran the Jaunty live CD, mounted the external, and then ran the install programme.  I allowed the external to be unmounted, and followed the friendly, colourful install guide.  There seemed to be no problems.  Upon reboot, however, Ubuntu refused to boot.

BIOS recognises the external drive and begins to boot from it.  grub appears to load, and after informing me that my external is a 1Tb Western Digital 10EADS, gives me these messages:
[0.360001] .. MP-BIOS bug: 8254 timer not connected to IO-APIC
[2.620032] ata1: softreset failed (device not ready)
modprobe: FATAL: could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory.

Then it says, "Loading.  Please wait..."  Which looks promising, and the Ubuntu splash screen comes up, but then, more bad news:
[INDENT]Gave up waiting for root device.
Common problems:

[LIST]
[*]Boot args (cat /proc/cmdline)
[LIST]
[*]Check rootdelay= (did system wait long enough?)
[*]check root= (did system wait for the right device?)
[/LIST]
[*]Missing modules (cat /proc/modules; ls /dev)
[/LIST]
ALERT! /dev/disk/by-uuid/28ea2cd7-bed8-4a13-8c1c-47a231dc20cd does not exist. dropping to a shell!
[/INDENT]
This starts "BusyBox," and gives me the prompt, (initramfs).

In BusyBox, I cat /proc/cmdline:
[INDENT]root=UUID=28ea2cd7-bed8-4a13-8c1c-47a231dc20cd ro quiet splash
[/INDENT]but there's no rootdelay= parameter.
cat /proc/modules yields a lot of information, but I don't know what it means:
[INDENT]ohci1394 38576 0 - Live 0xf7cdb000
ieee1394 94660 1 ohci1394 Live 0xf7ce1000
r8169 40836 0 - Live 0xf7cb6000
mii 13312 1 r8169, Live 0xf7c75000
fbcon 46112 0 - Live 0xf7ca8000
tileblit 10752 1 fbcon, Live 0xf7c94000
font 16384 1 fbcon, Live 0xf7c88000
bitblit 13824 1 fbcon, Live 0xf7c7b0000
softcursor 9984 1 bitblit, Live 0xf7c70000
[/INDENT]ls /dev/disk/by-uuid/ reveals that 28ea2cd7-bed8-4a13-8c1c-47a231dc20cd does not in fact exist.

Windows will still boot fine from the internal drive.

So, is there a compatability issue with the external or my laptop (Toshiba Satellite A215-S4807), did the install go awry, or is there an issue i can fix from the BusyBox prompt?  Or is it something else entirely (like booting from a USB external secretly doesn't work)?

---

