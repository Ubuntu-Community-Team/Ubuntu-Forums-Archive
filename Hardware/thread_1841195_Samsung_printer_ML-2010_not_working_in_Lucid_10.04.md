---
title: "Samsung printer ML-2010 not working in Lucid 10.04."
date: 2011-09-08
forum: Hardware
---

### Post by Craig P on 2011-09-08
I'm unable to get my Samsung printer ML-2010 to working with my new distro, Lucid 10.04 LTS.

With the printer plugged in by usb, and turned on of course:

I tried (System--Admin--Printing) localhost, but was unable get it working there, perhaps because I don't know the printer's URI. 


I also read up on this, and tried the terminal:  dmesg | tail -n40
The output is below. Any help is greatly appreciated!


craig@craig-desktop:~$ dmesg | tail -n40
[   15.880577]  domain 0: span 0-1 level MC
[   15.880580]   groups: 0 1
[   15.880587] CPU1 attaching sched-domain:
[   15.880589]  domain 0: span 0-1 level MC
[   15.880591]   groups: 1 0
[   20.732516] eth0: no IPv6 routers present
[   72.160027] Clocksource tsc unstable (delta = -291635844 ns)
[ 3210.336045] DMA write timed out
[ 3280.368041] parport0: FIFO is stuck
[ 3280.408037] parport0: BUSY timeout (1) in compat_write_block_pio
p0 releasing parport
[ 8140.948057] usb 2-8: new full speed USB device using ohci_hcd and address 3
[ 8141.164135] usb 2-8: configuration #1 chosen from 1 choice
[ 8141.765161] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04E8 pid 0x326C
[ 8141.765209] usbcore: registered new interface driver usblp
[ 8142.542015] usb 2-8: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[ 8144.511951] __ratelimit: 18 callbacks suppressed
[ 8144.511963] udev-configure-[2957]: segfault at 0 ip 0023c637 sp bfc489c8 error 4 in libc-2.11.1.so[1c2000+153000]

---

### Post by Craig P on 2011-09-08
p.s. Here is the complete output:

craig@craig-desktop:~$ dmesg | tail -n40
[   15.880577]  domain 0: span 0-1 level MC
[   15.880580]   groups: 0 1
[   15.880587] CPU1 attaching sched-domain:
[   15.880589]  domain 0: span 0-1 level MC
[   15.880591]   groups: 1 0
[   20.732516] eth0: no IPv6 routers present
[   72.160027] Clocksource tsc unstable (delta = -291635844 ns)
[ 3210.336045] DMA write timed out
[ 3280.368041] parport0: FIFO is stuck
[ 3280.408037] parport0: BUSY timeout (1) in compat_write_block_pio
[ 3290.408533] DMA write timed out
[ 3360.440646] parport0: FIFO is stuck
[ 3360.488217] parport0: BUSY timeout (1) in compat_write_block_pio
[ 3370.488039] DMA write timed out
[ 3440.536043] parport0: FIFO is stuck
[ 3440.584093] parport0: BUSY timeout (1) in compat_write_block_pio
[ 3450.584537] DMA write timed out
[ 3520.608039] parport0: FIFO is stuck
[ 3520.656036] parport0: BUSY timeout (1) in compat_write_block_pio
[ 3530.656063] DMA write timed out
[ 3600.676540] parport0: FIFO is stuck
[ 3600.724027] parport0: BUSY timeout (1) in compat_write_block_pio
[ 3610.724056] DMA write timed out
[ 3680.744032] parport0: FIFO is stuck
[ 3680.792033] parport0: BUSY timeout (1) in compat_write_block_pio
[ 3690.792050] DMA write timed out
[ 3760.820539] parport0: FIFO is stuck
[ 3760.868053] parport0: BUSY timeout (1) in compat_write_block_pio
[ 3770.868049] DMA write timed out
[ 3840.892035] parport0: FIFO is stuck
[ 3840.941320] parport0: BUSY timeout (1) in compat_write_block_pio
[ 3841.503035] parport0: BUSY timeout (-4) in compat_write_block_pio
[ 3841.503045] lp0 releasing parport
[ 8140.948057] usb 2-8: new full speed USB device using ohci_hcd and address 3
[ 8141.164135] usb 2-8: configuration #1 chosen from 1 choice
[ 8141.765161] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04E8 pid 0x326C
[ 8141.765209] usbcore: registered new interface driver usblp
[ 8142.542015] usb 2-8: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[ 8144.511951] __ratelimit: 18 callbacks suppressed
[ 8144.511963] udev-configure-[2957]: segfault at 0 ip 0023c637 sp bfc489c8 error 4 in libc-2.11.1.so[1c2000+153000]
craig@craig-desktop:~$

---

