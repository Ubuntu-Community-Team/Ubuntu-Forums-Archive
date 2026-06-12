---
title: "Problems with AACRAID on Trusty Thar"
date: 2016-07-11
forum: Hardware
---

### Post by David_Partridge on 2016-07-11
I've got an Adaptec ASR-51245 with a pair of SAS 4TB as a RAID 1 array.

The server is running as a home server, so I want to suspend it when not in use.  To this end I have installed powernap.

The problem is that when I resume the server from sleep I get errors reported for the raid card and the btrfs fs on that RAID:

```
Jul 11 00:18:51 Charon kernel: [49740.664384] ACPI: Low-level resume complete
Jul 11 00:18:51 Charon kernel: [49740.664384] PM: Restoring platform NVS memory
Jul 11 00:18:51 Charon kernel: [49740.664384] Enabling non-boot CPUs ...
Jul 11 00:18:51 Charon kernel: [49740.664384] x86: Booting SMP configuration:
Jul 11 00:18:51 Charon kernel: [49740.664384] smpboot: Booting Node 0 Processor 1 APIC 0x2
Jul 11 00:18:51 Charon kernel: [49740.676493]  cache: parent cpu1 should not be sleeping
Jul 11 00:18:51 Charon kernel: [49740.676753] CPU1 is up
Jul 11 00:18:51 Charon kernel: [49740.676830] smpboot: Booting Node 0 Processor 2 APIC 0x1
Jul 11 00:18:51 Charon kernel: [49740.688634]  cache: parent cpu2 should not be sleeping
Jul 11 00:18:51 Charon kernel: [49740.688898] CPU2 is up
Jul 11 00:18:51 Charon kernel: [49740.688956] smpboot: Booting Node 0 Processor 3 APIC 0x3
Jul 11 00:18:51 Charon kernel: [49740.700762]  cache: parent cpu3 should not be sleeping
Jul 11 00:18:51 Charon kernel: [49740.701036] CPU3 is up
Jul 11 00:18:51 Charon kernel: [49740.702585] ACPI: Waking up from system sleep state S3
Jul 11 00:18:51 Charon kernel: [49740.703493] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
Jul 11 00:18:51 Charon kernel: [49740.703587] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
Jul 11 00:18:51 Charon kernel: [49740.703648] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
Jul 11 00:18:51 Charon kernel: [49740.703727] uhci_hcd 0000:00:1d.3: System wakeup disabled by ACPI
Jul 11 00:18:51 Charon kernel: [49740.716447] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
Jul 11 00:18:51 Charon kernel: [49740.780406] PM: noirq resume of devices complete after 77.470 msecs
Jul 11 00:18:51 Charon kernel: [49740.781351] PM: early resume of devices complete after 0.782 msecs
Jul 11 00:18:51 Charon kernel: [49740.784279] usb usb2: root hub lost power or was reset
Jul 11 00:18:51 Charon kernel: [49740.784289] usb usb3: root hub lost power or was reset
Jul 11 00:18:51 Charon kernel: [49740.784351] usb usb4: root hub lost power or was reset
Jul 11 00:18:51 Charon kernel: [49740.784354] usb usb5: root hub lost power or was reset
Jul 11 00:18:51 Charon kernel: [49740.784497] pci 0000:00:1e.0: System wakeup disabled by ACPI
Jul 11 00:18:51 Charon kernel: [49740.788071] pciehp 0000:00:1c.1:pcie04: Timeout on hotplug command 0x1038 (issued 6073620 msec ago)
Jul 11 00:18:51 Charon kernel: [49740.788094] pciehp 0000:00:1c.0:pcie04: Timeout on hotplug command 0x1038 (issued 6073620 msec ago)
Jul 11 00:18:51 Charon kernel: [49740.788150] pciehp 0000:00:1c.3:pcie04: Timeout on hotplug command 0x1038 (issued 6073620 msec ago)
Jul 11 00:18:51 Charon kernel: [49740.791795] sd 3:0:0:0: [sdd] Starting disk
Jul 11 00:18:51 Charon kernel: [49740.797117] r8169 0000:04:0b.0 eth0: link down
Jul 11 00:18:51 Charon kernel: [49740.802066] i915: No ACPI video bus found
Jul 11 00:18:51 Charon kernel: [49740.892081] pciehp 0000:00:1c.0:pcie04: Device 0000:01:00.0 already exists at 0000:01:00, cannot hot-add
Jul 11 00:18:51 Charon kernel: [49740.892088] pciehp 0000:00:1c.0:pcie04: Cannot add device at 0000:01:00
Jul 11 00:18:51 Charon kernel: [49740.892103] pciehp 0000:00:1c.3:pcie04: Device 0000:03:00.0 already exists at 0000:03:00, cannot hot-add
Jul 11 00:18:51 Charon kernel: [49740.892110] pciehp 0000:00:1c.3:pcie04: Cannot add device at 0000:03:00
Jul 11 00:18:51 Charon kernel: [49740.892139] pciehp 0000:00:1c.1:pcie04: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add
Jul 11 00:18:51 Charon kernel: [49740.892145] pciehp 0000:00:1c.1:pcie04: Cannot add device at 0000:02:00
Jul 11 00:18:51 Charon kernel: [49740.892386] rtc_cmos 00:01: System wakeup disabled by ACPI
Jul 11 00:18:51 Charon kernel: [49740.894408] serial 00:02: activated
Jul 11 00:18:51 Charon kernel: [49741.036071] usb 1-6: reset high-speed USB device number 3 using ehci-pci
Jul 11 00:18:51 Charon kernel: [49741.108043] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 11 00:18:51 Charon kernel: [49741.108075] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 11 00:18:51 Charon kernel: [49741.108412] ata3.00: configured for UDMA/100
Jul 11 00:18:51 Charon kernel: [49741.116051] usb 3-1: reset full-speed USB device number 2 using uhci_hcd
Jul 11 00:18:51 Charon kernel: [49741.212049] ata7: SATA link down (SStatus 0 SControl 300)
Jul 11 00:18:51 Charon kernel: [49741.212096] ata8: SATA link down (SStatus 0 SControl 300)
Jul 11 00:18:51 Charon kernel: [49741.228874] ata4.00: configured for UDMA/100
Jul 11 00:18:51 Charon kernel: [49741.273420] PM: resume of devices complete after 492.059 msecs
Jul 11 00:18:51 Charon kernel: [49741.274628] PM: Finishing wakeup.
Jul 11 00:18:51 Charon bluetoothd[1059]: Adapter /org/bluez/1059/hci0 has been disabled
Jul 11 00:18:51 Charon bluetoothd[1059]: Unregister path: /org/bluez/1059/hci0
Jul 11 00:18:51 Charon kernel: [49741.274632] Restarting tasks ... done.
Jul 11 00:18:51 Charon bluetoothd[1059]: hci0: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
Jul 11 00:18:51 Charon bluetoothd[1059]: Adapter /org/bluez/1059/hci0 has been enabled
Jul 11 00:19:07 Charon kernel: [49757.197367] r8169 0000:04:0b.0 eth0: link up
Jul 11 00:19:22 Charon kernel: [49771.880029] aacraid: Host adapter abort request (0,1,2,0)
Jul 11 00:19:22 Charon kernel: [49771.880127] aacraid: Host adapter abort request (0,1,3,0)
Jul 11 00:19:53 Charon kernel: [49802.856031] aacraid: Host adapter abort request (0,1,3,0)
Jul 11 00:19:53 Charon kernel: [49802.856132] aacraid: Host adapter abort request (0,1,2,0)
Jul 11 00:20:08 Charon kernel: [49817.824074] aacraid: Host adapter abort request (0,0,0,0)
Jul 11 00:20:24 Charon kernel: [49833.824041] aacraid: Host adapter abort request (0,1,3,0)
Jul 11 00:20:24 Charon kernel: [49833.824116] aacraid: Host adapter abort request (0,1,2,0)
Jul 11 00:20:34 Charon kernel: [49843.824029] aacraid: Host adapter abort request (0,1,3,0)
Jul 11 00:20:44 Charon kernel: [49853.824035] aacraid: Host adapter abort request (0,1,2,0)
Jul 11 00:20:44 Charon kernel: [49853.824134] aacraid: Host adapter reset request. SCSI hang ?
Jul 11 00:20:44 Charon kernel: [49853.824142] AAC: Host adapter dead -3
Jul 11 00:20:44 Charon kernel: [49853.824152] sd 0:1:2:0: Device offlined - not ready after error recovery
Jul 11 00:20:44 Charon kernel: [49853.824159] sd 0:1:3:0: Device offlined - not ready after error recovery
Jul 11 00:20:44 Charon kernel: [49853.824165] sd 0:0:0:0: Device offlined - not ready after error recovery
Jul 11 00:20:44 Charon kernel: [49853.824223] sd 0:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
Jul 11 00:20:44 Charon kernel: [49853.824237] sd 0:0:0:0: [sda] CDB: Read(16) 88 00 00 00 00 00 00 1f 16 78 00 00 00 08 00 00
Jul 11 00:20:44 Charon kernel: [49853.824245] blk_update_request: I/O error, dev sda, sector 2037368
Jul 11 00:20:44 Charon kernel: [49853.824256] BTRFS: bdev /dev/sda1 errs: wr 0, rd 1, flush 0, corrupt 0, gen 0
Jul 11 00:20:44 Charon kernel: [49853.824854] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:20:44 Charon kernel: [49853.824877] BTRFS: bdev /dev/sda1 errs: wr 0, rd 2, flush 0, corrupt 0, gen 0
Jul 11 00:20:44 Charon kernel: [49853.824949] ------------[ cut here ]------------
Jul 11 00:20:44 Charon kernel: [49853.825017] WARNING: CPU: 2 PID: 913 at /build/linux-lts-wily-2axo4v/linux-lts-wily-4.2.0/fs/btrfs/extent-tree.c:2788 btrfs_run_delayed_refs.part.72+0x249/0x280 [btrfs]()
Jul 11 00:20:44 Charon kernel: [49853.825022] BTRFS: Transaction aborted (error -5)
Jul 11 00:20:44 Charon kernel: [49853.825027] Modules linked in: ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c ib_iser rdma_cm iw_cm ib_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi rfcomm bnep nfsd auth_rpcgss nfs_acl nfs lockd grace sunrpc fscache gpio_ich snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core arc4 coretemp snd_hwdep ath9k snd_pcm ath9k_common ath9k_hw ath btusb btrtl btbcm snd_seq_midi mac80211 btintel serio_raw snd_seq_midi_event snd_rawmidi bluetooth snd_seq cfg80211 lpc_ich snd_seq_device i915 snd_timer video drm_kms_helper snd drm 8250_fintek soundcore parport_pc shpchp mac_hid ppdev i2c_algo_bit lp parport btrfs xor raid6_pq pata_acpi psmouse r8169 mii aacraid ahci pata_jmicron libahci
Jul 11 00:20:44 Charon kernel: [49853.825182] CPU: 2 PID: 913 Comm: btrfs-transacti Not tainted 4.2.0-41-generic #48~14.04.1-Ubuntu
Jul 11 00:20:44 Charon kernel: [49853.825188] Hardware name:      /NM10, BIOS 080016  07/19/2011
Jul 11 00:20:44 Charon kernel: [49853.825194]  0000000000000000 ffff8800b8e93cc8 ffffffff817bbb8b ffff8800b8e93d18
Jul 11 00:20:44 Charon kernel: [49853.825205]  ffffffffc01683a8 ffff8800b8e93d08 ffffffff8107998a 0000000000000225
Jul 11 00:20:44 Charon kernel: [49853.825214]  ffff880079358e60 ffff880035837000 ffff88012e229d20 ffffffffffffffff
Jul 11 00:20:44 Charon kernel: [49853.825223] Call Trace:
Jul 11 00:20:44 Charon kernel: [49853.825239]  [<ffffffff817bbb8b>] dump_stack+0x63/0x81
Jul 11 00:20:44 Charon kernel: [49853.825252]  [<ffffffff8107998a>] warn_slowpath_common+0x8a/0xc0
Jul 11 00:20:44 Charon kernel: [49853.825263]  [<ffffffff81079a06>] warn_slowpath_fmt+0x46/0x50
Jul 11 00:20:44 Charon kernel: [49853.825326]  [<ffffffffc00d5039>] btrfs_run_delayed_refs.part.72+0x249/0x280 [btrfs]
Jul 11 00:20:44 Charon kernel: [49853.825384]  [<ffffffffc00d5087>] btrfs_run_delayed_refs+0x17/0x20 [btrfs]
Jul 11 00:20:44 Charon kernel: [49853.825441]  [<ffffffffc00e9bd5>] btrfs_commit_transaction+0x555/0xb30 [btrfs]
Jul 11 00:20:44 Charon kernel: [49853.825500]  [<ffffffffc00e4caa>] transaction_kthread+0x1ba/0x240 [btrfs]
Jul 11 00:20:44 Charon kernel: [49853.825559]  [<ffffffffc00e4af0>] ? btrfs_cleanup_transaction+0x560/0x560 [btrfs]
Jul 11 00:20:44 Charon kernel: [49853.825575]  [<ffffffff810979e9>] kthread+0xc9/0xe0
Jul 11 00:20:44 Charon kernel: [49853.825584]  [<ffffffff81097920>] ? kthread_create_on_node+0x1c0/0x1c0
Jul 11 00:20:44 Charon kernel: [49853.825594]  [<ffffffff817c341f>] ret_from_fork+0x3f/0x70
Jul 11 00:20:44 Charon kernel: [49853.825600]  [<ffffffff81097920>] ? kthread_create_on_node+0x1c0/0x1c0
Jul 11 00:20:44 Charon kernel: [49853.825606] ---[ end trace ea1d13c87ece298f ]---
Jul 11 00:20:44 Charon kernel: [49853.825614] BTRFS: error (device sda1) in btrfs_run_delayed_refs:2788: errno=-5 IO failure
Jul 11 00:20:44 Charon kernel: [49853.825621] BTRFS info (device sda1): forced readonly
Jul 11 00:20:44 Charon kernel: [49853.825627] BTRFS warning (device sda1): Skipping commit of aborted transaction.
Jul 11 00:20:44 Charon kernel: [49853.825632] BTRFS: error (device sda1) in cleanup_transaction:1710: errno=-5 IO failure
Jul 11 00:20:44 Charon anacron[14195]: Anacron 2.3 started on 2016-07-11
Jul 11 00:20:44 Charon anacron[14195]: Will run job `cron.daily' in 5 min.
Jul 11 00:20:44 Charon anacron[14195]: Jobs will be executed sequentially
Jul 11 00:21:21 Charon kernel: [49891.093251] init: anacron main process (14195) killed by TERM signal
Jul 11 00:22:18 Charon anacron[15767]: Anacron 2.3 started on 2016-07-11
Jul 11 00:22:18 Charon anacron[15767]: Will run job `cron.daily' in 5 min.
Jul 11 00:22:18 Charon anacron[15767]: Jobs will be executed sequentially
Jul 11 00:22:21 Charon kernel: [49950.779507] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.779524] BTRFS: bdev /dev/sda1 errs: wr 0, rd 3, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.779626] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.779635] BTRFS: bdev /dev/sda1 errs: wr 0, rd 4, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.780161] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.780175] BTRFS: bdev /dev/sda1 errs: wr 0, rd 5, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.780563] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.780575] BTRFS: bdev /dev/sda1 errs: wr 0, rd 6, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.781056] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.781067] BTRFS: bdev /dev/sda1 errs: wr 0, rd 7, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.783214] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.783228] BTRFS: bdev /dev/sda1 errs: wr 0, rd 8, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.783320] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.783333] BTRFS: bdev /dev/sda1 errs: wr 0, rd 9, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.783838] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.783849] BTRFS: bdev /dev/sda1 errs: wr 0, rd 10, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.789045] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.789062] BTRFS: bdev /dev/sda1 errs: wr 0, rd 11, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.789159] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.789169] BTRFS: bdev /dev/sda1 errs: wr 0, rd 12, flush 0, corrupt 0, gen 0
Jul 11 00:22:21 Charon kernel: [49950.789209] BTRFS info (device sda1): no csum found for inode 209219274 start 262144
Jul 11 00:22:21 Charon kernel: [49950.789229] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.789934] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.790012] BTRFS info (device sda1): no csum found for inode 209219274 start 307200
Jul 11 00:22:21 Charon kernel: [49950.790034] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.790678] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.790757] BTRFS info (device sda1): no csum found for inode 209219274 start 524288
Jul 11 00:22:21 Charon kernel: [49950.790779] sd 0:0:0:0: rejecting I/O to offline device
Jul 11 00:22:21 Charon kernel: [49950.791254] sd 0:0:0:0: rejecting I/O to offline device

   ... and lots more like that 

```

So is this an aacraid problem or a btrfs problem?  Or what?  Help!

Thanks
Dave

---

