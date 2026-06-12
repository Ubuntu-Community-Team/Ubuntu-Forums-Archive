---
title: "Upgraded to 7.10, SD reader doesn't work now"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by redashi on 2007-10-21
Greetings,

I've searched for this problem, but only found it back in 6.10. Upgraded to 7.10, now the Texas Instruments card reader doesn't work. I have a HP dv1519 (dv1000 series) laptop. Tried the TFIM workarounds, no go. It used to automatically mount and I could see it in my file manager. Also did the sdhci hack that worked before, no go. doing lspci the FlashMedia is 06:09.3. The hack is as follows:

mycomputer# more /etc/init.d/sdhci 
#!/bin/sh

# Get lsb functions
. /lib/lsb/init-functions

case "$1" in

start)
log_begin_msg "Configuring card reader"

modprobe fakephp || return 1
setpci -s 06:09.3 86.b=90
setpci -s 06:09.3 4c.b=02 # FlashMedia SD disable
setpci -s 06:09.3 04.b=06 # SDHCI Mem+ BusMaster+
setpci -s 06:09.3 88.b=01 # SDHCI DMA enable
modprobe sdhci || return 1

log_end_msg $?
;;

stop)
log_begin_msg "Shutting down card reader"

modprobe -r sdhci
lsmod | grep -q sdhci && return 1
setpci -s 06:09.3 88.b=00 # SDHCI DMA disable
setpci -s 06:09.3 04.b=07 # SDHCI Mem- BusMaster-
setpci -s 06:09.3 4c.b=00 # FlashMedia SD enable
setpci -s 06:09.3 86.b=d0
modprobe -r fakephp

log_end_msg $?
;;

*)
log_success_msg "Usage: /etc/init.d/sdhci start|stop"
exit 1
;;
esac

exit 0

did update-rc.d sdhci defaults. When I run /etc/init.d/sdhci start, the light flashes but I can't mount it and I see nothing in /media, or /mnt.

Any help? Would hate to back up now to the old kernel and old distro.

my /var/log/messages that look like it pertains:
 Oct 20 21:31:20 redashi-laptop kernel: [   38.764000] pci_hotplug: PCI Hot Plug 
PCI Core version: 0.5
Oct 20 21:31:20 redashi-laptop kernel: [   38.900000] fakephp: Fake PCI Hot Plug
 Controller Driver
Oct 20 21:31:20 redashi-laptop kernel: [   38.960000] tifm0 : demand removing ca
rd from socket 0:3
Oct 20 21:31:21 redashi-laptop kernel: [   39.632000] mmcblk0: mmc3:e624 SD02G 1
985024KiB 
Oct 20 21:31:21 redashi-laptop kernel: [   39.632000]  mmcblk0: p1
Oct 20 21:31:21 redashi-laptop kernel: [   39.812000] Failure registering capabi
lities with primary security module.

dmesg output: 
[ 2324.932000] mmc3: Timeout waiting for hardware interrupt.
[ 2324.932000] sdhci: ============== REGISTER DUMP ==============
[ 2324.932000] sdhci: Sys addr: 0x2625a000 | Version:  0x00008400
[ 2324.932000] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000000
[ 2324.932000] sdhci: Argument: 0x49230000 | Trn mode: 0x00000033
[ 2324.932000] sdhci: Present:  0x000f0001 | Host ctl: 0x00000003
[ 2324.932000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 2324.932000] sdhci: Wake-up:  0x00000000 | Clock:    0x00000003
[ 2324.932000] sdhci: Timeout:  0x00000006 | Int stat: 0x00000000
[ 2324.932000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
[ 2324.932000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 2324.932000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[ 2324.932000] sdhci: ===========================================
[ 2334.932000] mmc3: Timeout waiting for hardware interrupt.
[ 2334.932000] sdhci: ============== REGISTER DUMP ==============
[ 2334.932000] sdhci: Sys addr: 0x2625a000 | Version:  0x00008400
[ 2334.932000] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000000
[ 2334.932000] sdhci: Argument: 0x49230000 | Trn mode: 0x00000033
[ 2334.932000] sdhci: Present:  0x000f0001 | Host ctl: 0x00000003
[ 2334.932000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 2334.932000] sdhci: Wake-up:  0x00000000 | Clock:    0x00000003
[ 2334.932000] sdhci: Timeout:  0x00000006 | Int stat: 0x00000000
[ 2334.932000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
[ 2334.932000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 2334.932000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[ 2334.932000] sdhci: ===========================================

Something with the interrupts? 

Redashi

---

### Post by 00ber n00b on 2007-11-19
I have the same problem, what is the easiest way to get it to work?

---

