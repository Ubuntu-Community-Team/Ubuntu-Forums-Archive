---
title: "DVD unable to mount disc"
date: 2008-05-13
forum: Hardware
---

### Post by cousineaup on 2008-05-13
I've recently installed a fresh copy of Ubuntu 8.04 to replace Windows Vista. I got pretty much everything working right from the start but I'm still having trouble with one of my optical drives. My Plextor CD-RW can mount both data and audio discs but my Pioneer DVD-ROM cannot mount anything except data CDs. I've tried many different commercial DVDs, audio CDs and the like but nothing seem to work.

I've also tried without success to mount discs manually by running:

sudo mount -t udf /dev/scd1 /media/cdrom1

for which the output of dmesg | tail is:

[ 1545.869821] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1545.869825] sr 1:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 1545.869828] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1545.869831] end_request: I/O error, dev sr1, sector 64
[ 1545.870828] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1545.870832] sr 1:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 1545.870834] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1545.870838] end_request: I/O error, dev sr1, sector 64
[ 1560.569654] Inbound IN=eth0 OUT= MAC=00:11:d8:bc:73:d6:00:12:43:a9:ae:71:08:00 SRC=99.224.111.7 DST=99.224.174.171 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=58201 DF PROTO=TCP SPT=64523 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 1562.567753] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1562.567759] sr 1:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 1562.567763] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1562.567768] end_request: I/O error, dev sr1, sector 64
[ 1562.739110] end_request: I/O error, dev sr1, sector 16213832
[ 1562.783918] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1562.783924] sr 1:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 1562.783928] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1562.783932] end_request: I/O error, dev sr1, sector 128
[ 1562.784487] UDF-fs: No partition found (2)

I've read a number of similar threads and tried almost everything from installing additional libraries (such as libdvdcss2) and editing my /etc/fstab file but so far I've had little success. Any help from the Ubuntu Community would be greatly appreciated.

Pat

---

### Post by hermes0710 on 2008-05-14
Check this:
[http://club.cdfreaks.com/f44/sony-dru-720a-logical-unit-communication-crc-error-ultra-dma-32-040803-a-133258/]("http://club.cdfreaks.com/f44/sony-dru-720a-logical-unit-communication-crc-error-ultra-dma-32-040803-a-133258/")

It's not related to ubuntu (I think)

---

