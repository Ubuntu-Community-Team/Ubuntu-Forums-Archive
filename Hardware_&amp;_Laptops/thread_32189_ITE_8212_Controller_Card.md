---
title: "ITE 8212 Controller Card"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by linuxn00b on 2005-05-06
Hi there :)
I have been a ubuntuer (whatever ;)) since Hoary came out, and I love it. Only one problem: My controller card doesn't work :(.

I know that theres already a couple of threads about it here, but nothing really helped me.
If I try to compile the source from ITE's website it get around 1.000.000 errors.
If I try to patch the kernel with the -ac thingy and compile that i get errors, maybe I don't do it right?

If I do a "lspci", this is what I get (about the controller):
0000:00:0b.0 Unknown mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (PCI version seems to be IT8212, embedded seems (rev 11)

Hope someone can help.
Thank you!

---

### Post by theToolman on 2005-05-25
I too have tried a patch but it failed:

I tried to patch the 2.6.11 ubuntu patched kernel from the ubuntu repository with Alan Coxs patch-2.6.11-ac7.  I believe the ubuntu (including the debian patches as I understand it?) patches  include some conflicting updates to this -ac patch.    Or maybe I have done it wrong?  Comments welcomed :D

/usr/src/linux -> /usr/src/linux-source-2.6.11 BTW

toolman@toolpc:/usr/src/linux $ bzip2 -dc ~/installs/config/patch-2.6.11-ac7.bz2 | patch -p1 -t --dry-run
patching file arch/i386/Kconfig
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/i386/kernel/Makefile
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/i386/Makefile
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/ia64/kernel/fsys.S
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/ia64/kernel/signal.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/ppc/oprofile/op_model_fsl_booke.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/ppc/platforms/4xx/ebony.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/ppc/platforms/4xx/luan.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/ppc/platforms/4xx/ocotea.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/ppc64/kernel/irq.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file arch/um/kernel/skas/uaccess.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file Documentation/kernel-parameters.txt
Reversed (or previously applied) patch detected!  Assuming -R.
patching file Documentation/sysctl/kernel.txt
Reversed (or previously applied) patch detected!  Assuming -R.
patching file Documentation/tty.txt
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/cdrom/cdrom.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/char/digi1.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/char/digiFep1.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/char/drm/drm_ioctl.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/char/epca.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/char/epca.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/char/esp.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/char/Kconfig
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #1 succeeded at 151 (offset 13 lines).
Hunk #2 succeeded at 183 (offset 13 lines).
patching file drivers/char/stallion.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/char/watchdog/Makefile
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/i2c/chips/eeprom.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/arm/icside.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/cris/ide-v10.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/ide.c
Hunk #1 FAILED at 175.
Hunk #2 FAILED at 206.
Hunk #3 succeeded at 412 with fuzz 1 (offset 89 lines).
Hunk #4 FAILED at 546.
Hunk #5 FAILED at 565.
Hunk #6 FAILED at 581.
Hunk #7 FAILED at 745.
Hunk #8 FAILED at 800.
Hunk #9 FAILED at 819.
Hunk #10 FAILED at 861.
Hunk #11 FAILED at 882.
Hunk #12 FAILED at 923.
Hunk #13 FAILED at 947.
Hunk #14 succeeded at 1089 with fuzz 2 (offset 156 lines).
Hunk #15 succeeded at 1291 with fuzz 2 (offset 340 lines).
Hunk #16 FAILED at 1300.
Hunk #17 FAILED at 1413.
Hunk #18 FAILED at 1428.
Hunk #19 FAILED at 1440.
Hunk #20 FAILED at 1513.
Hunk #21 FAILED at 1551.
Hunk #22 FAILED at 1561.
Hunk #23 FAILED at 1569.
Hunk #24 FAILED at 1647.
Hunk #25 FAILED at 1846.
Hunk #26 FAILED at 1859.
Hunk #27 FAILED at 1917.
Hunk #28 FAILED at 2066.
Hunk #29 FAILED at 2075.
Hunk #30 FAILED at 2325.
Hunk #31 FAILED at 2460.
Hunk #32 FAILED at 2500.
Hunk #33 FAILED at 2511.
Hunk #34 FAILED at 2674.
Hunk #35 FAILED at 2700.
Hunk #36 FAILED at 2709.
Hunk #37 FAILED at 2742.
Hunk #38 FAILED at 2754.
Hunk #39 FAILED at 2794.
Hunk #40 FAILED at 2912.
37 out of 40 hunks FAILED -- saving rejects to file drivers/ide/ide.c.rej
patching file drivers/ide/ide-cd.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/ide-disk.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #2 succeeded at 211 (offset 1 line).
Hunk #3 succeeded at 221 (offset 1 line).
Hunk #4 succeeded at 440 (offset 2 lines).
Hunk #5 succeeded at 459 (offset 2 lines).
Hunk #6 succeeded at 637 (offset 2 lines).
Hunk #7 succeeded at 664 (offset 2 lines).
Hunk #8 succeeded at 683 (offset 2 lines).
Hunk #9 succeeded at 1055 (offset 2 lines).
patching file drivers/ide/ide-dma.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #1 succeeded at 133 (offset 1 line).
Hunk #2 succeeded at 923 (offset 1 line).
patching file drivers/ide/ide-floppy.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/ide-io.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #2 succeeded at 1441 (offset -1 lines).
patching file drivers/ide/ide-iops.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/ide-pnp.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/ide-probe.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/ide-proc.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/ide-tape.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/ide-taskfile.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/Kconfig
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/legacy/ide-cs.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/pci/alim15x3.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/pci/cs5520.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #3 succeeded at 224 with fuzz 2.
The next patch would create the file drivers/ide/pci/delkin_cb.c,
which already exists!  Assuming -R.
patching file drivers/ide/pci/delkin_cb.c
patching file drivers/ide/pci/generic.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #4 succeeded at 196 (offset 2 lines).
Hunk #5 succeeded at 220 (offset 2 lines).
Hunk #6 succeeded at 235 with fuzz 2 (offset 8 lines).
patching file drivers/ide/pci/hpt366.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #21 succeeded at 1054 (offset 7 lines).
Hunk #22 succeeded at 1072 (offset 7 lines).
Hunk #23 succeeded at 1100 (offset 7 lines).
Hunk #24 succeeded at 1155 (offset 7 lines).
Hunk #25 succeeded at 1204 (offset 7 lines).
Hunk #26 succeeded at 1234 (offset 7 lines).
Hunk #27 succeeded at 1276 (offset 7 lines).
Hunk #28 succeeded at 1305 (offset 7 lines).
Hunk #29 succeeded at 1325 (offset 7 lines).
Hunk #30 succeeded at 1345 (offset 7 lines).
Hunk #31 succeeded at 1407 (offset 7 lines).
Hunk #32 succeeded at 1435 (offset 7 lines).
Hunk #33 succeeded at 1450 (offset 7 lines).
Hunk #34 succeeded at 1477 (offset 7 lines).
Hunk #35 succeeded at 1487 (offset 7 lines).
Hunk #36 succeeded at 1509 (offset 7 lines).
Hunk #37 succeeded at 1533 (offset 7 lines).
Hunk #38 succeeded at 1542 (offset 7 lines).
Hunk #39 succeeded at 1566 (offset 7 lines).
Hunk #40 succeeded at 1653 (offset 7 lines).
Hunk #41 succeeded at 1663 (offset 7 lines).
Hunk #42 succeeded at 1672 (offset 7 lines).
Hunk #43 succeeded at 1681 (offset 7 lines).
Hunk #44 succeeded at 1690 (offset 7 lines).
Hunk #45 succeeded at 1699 (offset 7 lines).
The next patch would create the file drivers/ide/pci/it821x.c,
which already exists!  Assuming -R.
patching file drivers/ide/pci/it821x.c
patching file drivers/ide/pci/Makefile
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/pci/ns87415.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/pci/pdc202xx_old.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/pci/sgiioc4.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/pci/siimage.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #3 succeeded at 1112 (offset 2 lines).
patching file drivers/ide/pci/sl82c105.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/pci/trm290.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/ppc/pmac.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/ide/setup-pci.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/input/keyboard/atkbd.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/input/serio/i8042.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/input/serio/i8042-x86ia64io.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/macintosh/mediabay.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/md/raid6altivec.uc
Hunk #1 FAILED at 108.
1 out of 1 hunk FAILED -- saving rejects to file drivers/md/raid6altivec.uc.rej
patching file drivers/media/video/adv7170.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/media/video/adv7175.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/media/video/bt819.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/media/video/saa7110.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/media/video/saa7114.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/media/video/saa7185.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/net/amd8111e.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/net/pcnet32.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/net/ppp_async.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/net/r8169.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #1 succeeded at 1639 (offset -44 lines).
Hunk #2 succeeded at 1668 (offset -44 lines).
Hunk #3 succeeded at 2108 with fuzz 1 (offset -42 lines).
patching file drivers/net/sis900.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/net/tulip/media.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/net/tulip/tulip_core.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/net/tun.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/net/via-rhine.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/net/wan/hd6457x.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/pci/hotplug/pciehp_ctrl.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/pci/pci.ids
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/scsi/ahci.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #1 succeeded at 528 (offset -10 lines).
Hunk #2 succeeded at 560 (offset -10 lines).
patching file drivers/scsi/atp870u.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/scsi/atp870u.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/scsi/ide-scsi.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/scsi/Kconfig
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #1 succeeded at 291 (offset 18 lines).
patching file drivers/scsi/nsp32.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file drivers/usb/media/Kconfig
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #1 succeeded at 161 (offset -14 lines).
patching file drivers/usb/media/Makefile
Reversed (or previously applied) patch detected!  Assuming -R.
The next patch would create the file drivers/usb/media/pwc/ChangeLog,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/ChangeLog
The next patch would create the file drivers/usb/media/pwc/Makefile,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/Makefile
Hunk #1 FAILED at 1.
File drivers/usb/media/pwc/Makefile is not empty after patch, as expected
1 out of 1 hunk FAILED -- saving rejects to file drivers/usb/media/pwc/Makefile.rej
The next patch would create the file drivers/usb/media/pwc/pwc-ctrl.c,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-ctrl.c
Hunk #1 FAILED at 1.
File drivers/usb/media/pwc/pwc-ctrl.c is not empty after patch, as expected
1 out of 1 hunk FAILED -- saving rejects to file drivers/usb/media/pwc/pwc-ctrl.c.rej
The next patch would create the file drivers/usb/media/pwc/pwc-dec1.c,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-dec1.c
The next patch would create the file drivers/usb/media/pwc/pwc-dec1.h,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-dec1.h
The next patch would create the file drivers/usb/media/pwc/pwc-dec23.c,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-dec23.c
The next patch would create the file drivers/usb/media/pwc/pwc-dec23.h,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-dec23.h
The next patch would create the file drivers/usb/media/pwc/pwc.h,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc.h
Hunk #1 FAILED at 1.
File drivers/usb/media/pwc/pwc.h is not empty after patch, as expected
1 out of 1 hunk FAILED -- saving rejects to file drivers/usb/media/pwc/pwc.h.rej
The next patch would create the file drivers/usb/media/pwc/pwc-if.c,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-if.c
Hunk #1 FAILED at 1.
File drivers/usb/media/pwc/pwc-if.c is not empty after patch, as expected
1 out of 1 hunk FAILED -- saving rejects to file drivers/usb/media/pwc/pwc-if.c.rej
The next patch would create the file drivers/usb/media/pwc/pwc-ioctl.h,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-ioctl.h
The next patch would create the file drivers/usb/media/pwc/pwc-kiara.c,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-kiara.c
The next patch would create the file drivers/usb/media/pwc/pwc-kiara.h,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-kiara.h
The next patch would create the file drivers/usb/media/pwc/pwc-misc.c,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-misc.c
Hunk #1 FAILED at 1.
File drivers/usb/media/pwc/pwc-misc.c is not empty after patch, as expected
1 out of 1 hunk FAILED -- saving rejects to file drivers/usb/media/pwc/pwc-misc.c.rej
The next patch would create the file drivers/usb/media/pwc/pwc-nala.h,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-nala.h
The next patch would create the file drivers/usb/media/pwc/pwc-timon.c,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-timon.c
The next patch would create the file drivers/usb/media/pwc/pwc-timon.h,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-timon.h
The next patch would create the file drivers/usb/media/pwc/pwc-uncompress.c,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-uncompress.c
The next patch would create the file drivers/usb/media/pwc/pwc-uncompress.h,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/pwc-uncompress.h
The next patch would create the file drivers/usb/media/pwc/philips.txt,
which already exists!  Assuming -R.
patching file drivers/usb/media/pwc/philips.txt
patching file fs/binfmt_elf.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #1 succeeded at 1007 (offset -1 lines).
Hunk #2 succeeded at 1030 (offset -1 lines).
patching file fs/cramfs/inode.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file fs/exec.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file fs/ext2/dir.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file fs/isofs/inode.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file fs/isofs/rock.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file fs/jbd/transaction.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file fs/proc/base.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file include/asm-i386/ide.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file include/asm-i386/param.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file include/linux/binfmts.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file include/linux/hayesesp.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file include/linux/ide.h
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #11 succeeded at 1131 with fuzz 1 (offset 1 line).
Hunk #12 succeeded at 1344 (offset 2 lines).
Hunk #13 succeeded at 1446 (offset 2 lines).
patching file include/linux/irq.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file include/linux/pci_ids.h
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #5 succeeded at 2424 (offset -3 lines).
patching file include/linux/sched.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file include/linux/stallion.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file include/linux/sysctl.h
Reversed (or previously applied) patch detected!  Assuming -R.
patching file kernel/irq/handle.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file kernel/irq/spurious.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file kernel/signal.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file kernel/sys.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file kernel/sysctl.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file lib/rwsem.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file lib/rwsem-spinlock.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file Makefile
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/802/tr.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/bluetooth/af_bluetooth.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/bridge/br_ioctl.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/ipv4/fib_hash.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/ipv4/tcp_input.c
Reversed (or previously applied) patch detected!  Assuming -R.
Hunk #1 succeeded at 1652 (offset -1 lines).
patching file net/ipv4/tcp_timer.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/ipv4/xfrm4_output.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/ipv6/xfrm6_output.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/netrom/nr_in.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/rose/rose_route.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file net/xfrm/xfrm_state.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file security/commoncap.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file security/dummy.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file sound/core/timer.c
Reversed (or previously applied) patch detected!  Assuming -R.
patching file sound/pci/ac97/ac97_codec.c
Reversed (or previously applied) patch detected!  Assuming -R.
toolman@toolpc:/usr/src/linux $

---

