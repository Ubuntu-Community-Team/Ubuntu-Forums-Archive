---
title: "CD/DVD mount problem"
date: 2010-10-13
forum: Hardware
---

### Post by x53x6ex69x67x67x65x72 on 2010-10-13
Hi
I'm using Ubuntu 10.04 (lucid lynx).
Sometimes it doesn't detect CD/DVD when I insert them.
For example today I inserted a VCD and it mounted correctly.
But After that (without system reboot) i tried a DVD but it doesn't mount automatically!
When I insert CD/DVD system writes this in "syslog":
```

Oct 13 23:08:51 ariyan-laptop pulseaudio[1759]: ratelimit.c: 87 events suppressed
Oct 13 23:09:01 ariyan-laptop CRON[11847]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct 13 23:09:51 ariyan-laptop pulseaudio[1759]: ratelimit.c: 84 events suppressed
Oct 13 23:11:56 ariyan-laptop kernel: [39468.382150] sr 1:0:0:0: [sr0] Unhandled sense code
Oct 13 23:11:56 ariyan-laptop kernel: [39468.382155] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 13 23:11:56 ariyan-laptop kernel: [39468.382161] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Oct 13 23:11:56 ariyan-laptop kernel: [39468.382168] sr 1:0:0:0: [sr0] Add. Sense: Cannot read medium - unknown format
Oct 13 23:11:56 ariyan-laptop kernel: [39468.382177] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Oct 13 23:11:56 ariyan-laptop kernel: [39468.382193] end_request: I/O error, dev sr0, sector 0
Oct 13 23:11:56 ariyan-laptop kernel: [39468.382199] __ratelimit: 129 callbacks suppressed
Oct 13 23:11:56 ariyan-laptop kernel: [39468.382203] Buffer I/O error on device sr0, logical block 0

```

And when I try to mount it manually it writes:
```

Oct 13 23:07:27 ariyan-laptop kernel: [39200.076178] sr 1:0:0:0: [sr0] Unhandled sense code
Oct 13 23:07:27 ariyan-laptop kernel: [39200.076183] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 13 23:07:27 ariyan-laptop kernel: [39200.076189] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Oct 13 23:07:27 ariyan-laptop kernel: [39200.076196] sr 1:0:0:0: [sr0] Add. Sense: Cannot read medium - unknown format
Oct 13 23:07:27 ariyan-laptop kernel: [39200.076205] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 10 00 00 01 00
Oct 13 23:07:27 ariyan-laptop kernel: [39200.076221] end_request: I/O error, dev sr0, sector 64
Oct 13 23:07:27 ariyan-laptop kernel: [39200.076372] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```

when I reboot system it works correctly again!
What's on?
how can I fix it?

---

### Post by x53x6ex69x67x67x65x72 on 2010-10-15
Hi again
this problem is reported on launchpad as I searched but none of them had any solution!
The strange thing is now I have a DVD that doesn't mount at all !! and gives those errors ! but the other DVDs mount without problem!
I thought DVD is corrupted so I found a windows machine and made an ISO image from DVD and transfered it to my Linux box.
The ISO image mounts correctly without problem , Just the disk has that problem! 

Can anyone suggest me a solution? 

Thanks

---

