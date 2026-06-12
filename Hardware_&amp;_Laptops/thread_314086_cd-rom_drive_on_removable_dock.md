---
title: "cd-rom drive on removable dock"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by klock on 2006-12-07
So I have been having this problem for a little while.

I have a Compaq n400c with its removable mec. It contains both a cd-rom drive (/dev/hdc) and a floppy drive (/dev/fd0)

The problem is I can use both of these drives when I boot the machine with the mec attached. But what is the point of having an mec if you cant just attach it and use the drives whenever.

So:

When I add the dock, the machine allows me to use fd0 but will say that /dev/hdc does not exist. I was wondering if anyone has a laptop with a similiar configuration and can point me in a direction of figuring out how to get it to I guess "locate" or "create" /dev/hdc when the mec is attached?

(Bear with my phrasing, Im still a novice Linux user. But I do try)

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3 -- converted during upgrade to edgy
UUID=2cfb871a-9aaa-4b96-adae-47b03ca18051 / ext3 noatime,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=92d072a4-4ec9-4097-a073-58d2c9b7b32a /boot ext2 defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=61072a04-cdbd-4c3a-929b-41b13e57db01 /home ext3 noatime 0 2
# /dev/hda8 -- converted during upgrade to edgy
UUID=a4ec9aad-7284-4e93-b476-6dfb32dc242c /tmp ext3 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=1d3763f9-730f-490c-ac59-fdd4b8e08cb8 /usr ext3 noatime 0 2
# /dev/hda7 -- converted during upgrade to edgy
UUID=1ff6ad5a-6332-4fce-8146-af1b95142fed /var ext3 noatime 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=cb5df965-a955-40dd-ab76-57f73190f4d4 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


klock@FUCKUP:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1211
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
00:09.1 Serial controller: Agere Systems LT WinModem
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

kernel: 2.6.17-10-386

Im on edgy also.

If you need any more information, post and I will retreive it for you.

---

