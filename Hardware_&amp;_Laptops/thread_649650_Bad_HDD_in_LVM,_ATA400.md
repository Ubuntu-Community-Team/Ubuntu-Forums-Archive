---
title: "Bad HDD in LVM, ATA4:00"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by Centx on 2007-12-25
I have a LVM-setup with 4 physical disks (3 WD 320 GB and one Samsung 500GB) and for quite some time now, whenever it does a fsck on bootup on the lvm-pool  (done 20 boots etc) it chrashes or hangs up.
I get a whole lot of errors mentioning ATA4:00, and well:
```

root@xeon:~# grep -i ata3 /var/log/messages|wc
     50     770    5020
root@xeon:~# grep -i ata4 /var/log/messages|wc
   1233   15197   96740

```

as you can see, there is roughly 1200 more lines mentioning ata4 than ata3, which I believe has not gone bad. most of those 1200 lines are ```
Dec 24 23:40:03 Xeon kernel: [ 1399.435412] ata4.00: configured for UDMA/33
Dec 24 23:40:03 Xeon kernel: [ 1399.435424] ata4: EH complete
Dec 24 23:40:04 Xeon kernel: [ 1400.788372] ata4: soft resetting port
Dec 24 23:40:04 Xeon kernel: [ 1400.944115] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

```

I'm wondering how to find out what disk (/dev/sdX) ata4(:00) is, and I'm thinking about just mounting the lvm-disk, moving some stuff over on a usb-disk, remove the (assumed) bad disk from the array, and going from there.

Any ideas are welcomed on how to solve this problem in other ways though, and info about how to determine if this is actually a bad disk or cable or whatever would also be very useful.

Thanks in Advance! =9

EDIT:
This [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147858]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147858") has led me to believe it might have something with NCQ or something to do.

It is a lot more where this came from =/
```

Dec 23 02:00:22 Xeon kernel: [49341.728857] ata4: soft resetting port
Dec 23 02:00:23 Xeon kernel: [49341.884622] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 02:00:23 Xeon kernel: [49341.925041] ata4.00: configured for UDMA/133
Dec 23 02:00:23 Xeon kernel: [49341.925056] ata4: EH complete
Dec 23 02:00:23 Xeon kernel: [49342.351836] ata4: soft resetting port
Dec 23 02:00:23 Xeon kernel: [49342.507578] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 02:00:23 Xeon kernel: [49342.555955] ata4.00: configured for UDMA/133
Dec 23 02:00:23 Xeon kernel: [49342.555967] ata4: EH complete
Dec 23 02:00:32 Xeon kernel: [49350.889596] ata4: soft resetting port
Dec 23 02:00:32 Xeon kernel: [49351.045356] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 02:00:32 Xeon kernel: [49351.093753] ata4.00: configured for UDMA/133
Dec 23 02:00:32 Xeon kernel: [49351.093765] ata4: EH complete
Dec 23 02:00:32 Xeon kernel: [49351.132169] ata4.00: limiting speed to UDMA/100:PIO4
Dec 23 02:00:32 Xeon kernel: [49351.440674] ata4: soft resetting port
Dec 23 02:00:32 Xeon kernel: [49351.596437] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 02:00:32 Xeon kernel: [49351.640908] ata4.00: configured for UDMA/100
Dec 23 02:00:32 Xeon kernel: [49351.640920] ata4: EH complete
Dec 23 02:00:33 Xeon kernel: [49352.810394] ata4: soft resetting port
Dec 23 02:00:34 Xeon kernel: [49352.966153] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 02:00:34 Xeon kernel: [49353.006546] ata4.00: configured for UDMA/100
Dec 23 02:00:34 Xeon kernel: [49353.006557] ata4: EH complete
Dec 23 02:00:34 Xeon kernel: [49353.373455] ata4: soft resetting port
Dec 23 02:00:34 Xeon kernel: [49353.529228] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 02:00:34 Xeon kernel: [49353.577603] ata4.00: configured for UDMA/100
Dec 23 02:00:34 Xeon kernel: [49353.577618] ata4: EH complete
Dec 23 02:00:39 Xeon kernel: [49358.816386] ata4: soft resetting port
Dec 23 02:00:40 Xeon kernel: [49358.972150] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 02:00:40 Xeon kernel: [49359.016546] ata4.00: configured for UDMA/100
Dec 23 02:00:40 Xeon kernel: [49359.016558] ata4: EH complete
Dec 23 02:00:40 Xeon kernel: [49359.067233] ata4.00: limiting speed to UDMA/33:PIO4
Dec 23 02:00:40 Xeon kernel: [49359.375462] ata4: soft resetting port
Dec 23 02:00:40 Xeon kernel: [49359.531217] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 02:00:40 Xeon kernel: [49359.575605] ata4.00: configured for UDMA/33
Dec 23 02:00:40 Xeon kernel: [49359.575621] ata4: EH complete

```

---

