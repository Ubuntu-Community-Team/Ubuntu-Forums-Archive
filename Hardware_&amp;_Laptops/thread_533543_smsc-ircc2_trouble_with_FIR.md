---
title: "smsc-ircc2 trouble with FIR"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by lukaszd on 2007-08-24
Hello there,

I have a problem configuring smsc-ircc2 with my Acer Aspire 2012WLMI. The SMC chip inside the Acer reportedly supports FIR. I have enabled it in BIOS and then - with a little help of smcinit - configured the module to run with the following options:

options smsc-ircc2 ircc_dma=3 ircc_irq=3 ircc_cfg=0x2e ircc_sir=0x3f8 ircc_fir=0x130

The module is loaded by irda-utils at boot (with smcinit run just before) and SIR communications work flawlessly.

The problem is when I want to enable FIR. I have a SE K550i that supports speeds up to 1150kbps and as it works well with Windows at ~60kB/s I wanted to speed up its chats with the Acer, too. With sysctl I set /proc/sys/net/irda/max_baud_rate to 1152000 and tried to send something over to the phone. Here's irdadump's output:

06:59:59.693517 xid:cmd 82da70ed > ffffffff S=6 s=* czarny hint=0400 [ Computer ] (22)
07:00:02.164421 xid:cmd 82da70ed > ffffffff S=6 s=0 (14)
07:00:02.252379 xid:cmd 82da70ed > ffffffff S=6 s=1 (14)
07:00:02.342480 xid:rsp 82da70ed < 289fe29c S=6 s=1 Sony Ericss hint=9124 [ PnP Modem IrCOMM IrOBEX ] (28)
07:00:02.352339 xid:cmd 82da70ed > ffffffff S=6 s=2 (14)
07:00:02.440296 xid:cmd 82da70ed > ffffffff S=6 s=3 (14)
07:00:02.528268 xid:cmd 82da70ed > ffffffff S=6 s=4 (14)
07:00:02.616224 xid:cmd 82da70ed > ffffffff S=6 s=5 (14)
07:00:02.704186 xid:cmd 82da70ed > ffffffff S=6 s=* czarny hint=0400 [ Computer ] (22)
07:00:04.690328 snrm:cmd ca=fe pf=1 82da70ed > 289fe29c new-ca=8a
        LAP QoS: Baud Rate=1152000bps Max Turn Time=500ms Data Size=2048B Window Size=3 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (32)
07:00:04.805171 ua:rsp ca=8a pf=1 82da70ed < 289fe29c
        LAP QoS: Baud Rate=1152000bps Max Turn Time=500ms Data Size=256B Window Size=3 Add BOFS=2 Min Turn Time=1000us Link Disc=12s (31)
07:00:04.805298 rr:cmd > ca=8a pf=1 nr=0 (2)

And then it freezes completely. The phone never signals anything, ircp aborts with "connection failed" and irdadump no longer shows anything until smcinit is invoked and irda-utils restarted. Dmesg shows the following:

[  536.136000] smsc_ircc_change_speed() changing speed to: 1152000
[  536.136000] smsc_ircc_set_fir_speed(), handling baud of 1152000
[  538.884000] IrLAP, no activity on link!
[  541.020000] irlmp_state_setup() WATCHDOG_TIMEOUT!
[  541.020000] irda_connect(), connect failed!
[  541.884000] IrLAP, no activity on link!
[  544.884000] IrLAP, no activity on link!
[  547.884000] IrLAP, no activity on link!
[  548.384000] irlap_change_speed(), setting speed to 9600

I've tried tweaking the window size, the turn time, the data size - to no avail.

I'd appreciate any help!

Thanks,
Lukasz

---

