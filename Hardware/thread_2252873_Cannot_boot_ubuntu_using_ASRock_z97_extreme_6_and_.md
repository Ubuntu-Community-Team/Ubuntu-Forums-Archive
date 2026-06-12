---
title: "Cannot boot ubuntu using ASRock z97 extreme 6 and core i7 4690K"
date: 2014-11-15
forum: Hardware
---

### Post by zircon_34 on 2014-11-15
Just build up a new linux box and the components should be compatible. Its a ASRock Z97 extreme 6 motherboard and core i7 4790K. No windows install at all.
 
However, I tried to boot using a live USB on the USB3 port or alternatively using a DVD, ubuntu tries to starts for 3 sec and then hangs and I have a black screen, nothing happens. I connected my monitor via HDMI, but that cannot be the issue as when I start I can boot in UEFI and see it on my monitor. Secure boot is disabled.

Does anyone know if I should update the UEFI firmware first? or this may be related to something else?

I will keep the post updated if I find a solution.

---

### Post by oldfred on 2014-11-15
Make sure you are not using any asmedia ports.

Other Asrock threads.
 ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

I just built a new system with Asus AR. I had to upgrade UEFI and change a lot of UEFI settings. It had Windows or other which I assumed really meant secure boot. But with Asus all the UEFI settings are under the CSM sub menu, not a separate menu. I had to keep a list of changes, but with UEFI it does tell you what settings changed.

---

### Post by zircon_34 on 2014-11-15
Thanks for the links oldfred! I also suspect it has to do with the asmedia ports. I found this thread, but havent tried yet:
[http://forums.tweaktown.com/asrock/58840-z97-extreme6-wont-boot-asmedia-sata-controller-enabled.html](http://forums.tweaktown.com/asrock/58840-z97-extreme6-wont-boot-asmedia-sata-controller-enabled.html)

But disabling ports is not a long term solution...

---

### Post by zircon_34 on 2014-11-15
Ok, managed to live boot the USB! This thread helped:[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6/page2]("http://ubuntuforums.org/showthread.php?t=2252873")

What I did: a) Press F2 and go in UEFI menu, b) Advanced/Storage configuration/ASMedia SATA3 Mode and disable it.

I could not boot the dvd, but the live USB worked and booted into Ubuntu gnome 14.04;), I might have to plug my CD/DVD drive in another Sata port.

Anyone knows a fix to enable ASMedia Sata ports let me know!

---

