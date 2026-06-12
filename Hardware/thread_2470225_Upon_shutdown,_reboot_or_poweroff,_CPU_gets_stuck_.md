---
title: "Upon shutdown, reboot or poweroff, CPU gets stuck on SiFive Unmatched"
date: 2021-12-22
forum: Hardware
---

### Post by bloudraak on 2021-12-22
I'm installed Ubuntu Server 21.04 (Kernel 21.04 5.11.0-1023-generic) on a SiFive Unmatched board, using [these instructions]("https://ubuntu.com/tutorials/how-to-install-ubuntu-on-risc-v-hifive-boards#1-overview"). However, I noticed that I'm unable to reboot the host, with it being stuck with the following. 

```
[  OK  ] Finished Reboot.
[  OK  ] Reached target Reboot.
[ 4135.181790] reboot: Restarting system
[ 4160.023449] watchdog: BUG: soft lockup - CPU#0 stuck for 23s! [shutdown:1]
[ 4160.029580] Modules linked in: nls_iso8859_1 dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua da9063_onkey lm90 uio_pdrv_genirq uio sch_fq_codel drm backlight ip_tables x_tables autofs4 btrfs blake2b_generic raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear mscc macsec nvme rtc_da9063 da9063_regulator macb xhci_pci nvme_core xhci_pci_renesas phylink i2c_ocores
[ 4160.068255] CPU: 0 PID: 1 Comm: shutdown Tainted: G        W         5.11.0-1023-generic #24-Ubuntu
[ 4160.077264] epc: ffffffe000004ce0 ra : ffffffe000004ce0 sp : ffffffe08005bd40
[ 4160.084383]  gp : ffffffe001c14290 tp : ffffffe080056780 t0 : ffffffe001c26157
[ 4160.091593]  t1 : ffffffe001c26148 t2 : 0000000000000000 s0 : ffffffe08005bd60
[ 4160.098803]  s1 : 0000000000000000 a0 : 0000000000000000 a1 : 0000000000000000
[ 4160.106011]  a2 : 0000000000000000 a3 : 0000000000000000 a4 : f77677bed53b9d00
[ 4160.113221]  a5 : f77677bed53b9d00 a6 : 0000000000000028 a7 : ffffffe00055a8aa
[ 4160.120430]  s2 : 0000000028121969 s3 : ffffffe001a1f100 s4 : fffffffffee1dead
[ 4160.127639]  s5 : ffffffe001c170c0 s6 : 62f35e596a37af00 s7 : 0000002ad5d98bf0
[ 4160.134858]  s8 : 0000000000000000 s9 : 0000000000000000 s10: 0000000000000fff
[ 4160.142068]  s11: 0000000000080080 t3 : 0000000000000072 t4 : ffffffffffffffff
[ 4160.149277]  t5 : 0000000000000009 t6 : ffffffe08005ba98
[ 4160.154568] status: 0000000200000120 badaddr: 0000000000000000 cause: 8000000000000005
[ 4184.023399] watchdog: BUG: soft lockup - CPU#0 stuck for 22s! [shutdown:1]
[ 4184.029536] Modules linked in: nls_iso8859_1 dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua da9063_onkey lm90 uio_pdrv_genirq uio sch_fq_codel drm backlight ip_tables x_tables autofs4 btrfs blake2b_generic raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear mscc macsec nvme rtc_da9063 da9063_regulator macb xhci_pci nvme_core xhci_pci_renesas phylink i2c_ocores
[ 4184.068232] CPU: 0 PID: 1 Comm: shutdown Tainted: G        W    L    5.11.0-1023-generic #24-Ubuntu
[ 4184.077222] epc: ffffffe000004ce0 ra : ffffffe000004ce0 sp : ffffffe08005bd40
[ 4184.084337]  gp : ffffffe001c14290 tp : ffffffe080056780 t0 : ffffffe001c26157
[ 4184.091552]  t1 : ffffffe001c26148 t2 : 0000000000000000 s0 : ffffffe08005bd60
[ 4184.098761]  s1 : 0000000000000000 a0 : 0000000000000000 a1 : 0000000000000000
[ 4184.105971]  a2 : 0000000000000000 a3 : 0000000000000000 a4 : f77677bed53b9d00
[ 4184.113180]  a5 : f77677bed53b9d00 a6 : 0000000000000028 a7 : ffffffe00055a8aa
[ 4184.120389]  s2 : 0000000028121969 s3 : ffffffe001a1f100 s4 : fffffffffee1dead
[ 4184.127598]  s5 : ffffffe001c170c0 s6 : 62f35e596a37af00 s7 : 0000002ad5d98bf0
[ 4184.134808]  s8 : 0000000000000000 s9 : 0000000000000000 s10: 0000000000000fff
[ 4184.142017]  s11: 0000000000080080 t3 : 0000000000000072 t4 : ffffffffffffffff
[ 4184.149226]  t5 : 0000000000000009 t6 : ffffffe08005ba98
[ 4184.154518] status: 0000000200000120 badaddr: 0000000000000000 cause: 8000000000000005
[ 4195.187376] rcu: INFO: rcu_sched self-detected stall on CPU
[ 4195.192198] rcu:     0-....: (14933 ticks this GP) idle=812/1/0x4000000000000002 softirq=36573/36573 fqs=7501 
[ 4195.201931]  (t=15004 jiffies g=55581 q=153)
[ 4195.206217] Call Trace:


```

The only thing that seems to work is to manually poweroff the device, and then start it. That is less than ideal for automation (e.g. automatically update and reboot), or remote management. 

Just wondering if this is a known issue and if there's a workaround for this issue.

---

