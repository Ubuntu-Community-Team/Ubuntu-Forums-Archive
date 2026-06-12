---
title: "ahci causing kernel panic"
date: 2008-10-22
forum: General Help
---

### Post by hakr89 on 2008-10-22
I have been having problems with my machine crashing.

This time I was able to redirect the kernel messages to the serial port so I could catch the kernel panic (this machine doesn't have a video card).

```

[156551.343608] BUG: unable to handle kernel paging request at virtual address 3cd8500a
[156551.351482] printing eip: c031c4a9 *pde = 00000000 
[156551.356586] Oops: 0002 [#1] SMP 
[156551.359986] Modules linked in: loop xt_state ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nfsd auth_rpcgss exportfs ppdev tun container dock video output battery sbs sbshc xt_TCPMSS xt_tcpmss xt_tcpudp iptable_mangle nfs lockd nfs_acl sunrpc pppoe pppox af_packet ppp_generic slhc iptable_filter ip_tables x_tables ext2 ac lp dvb_pll nxt200x saa7134_dvb videobuf_dvb dvb_core tda1004x tuner tea5767 tda8290 tuner_simple mt20xx tea5761 ipv6 saa7134 compat_ioctl32 videobuf_dma_sg videobuf_core ir_kbd_i2c i2c_core ir_common videodev v4l2_common v4l1_compat typhoon button intel_agp shpchp iTCO_wdt iTCO_vendor_support pci_hotplug agpgart evdev parport_pc parport pcspkr ext3 jbd mbcache pata_jmicron sg sd_mod usb_storage libusual pata_acpi ahci ata_generic r8169 libata scsi_mod ehci_hcd uhci_hcd usbcore raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
[156551.450376] 
[156551.451985] Pid: 0, comm: swapper Not tainted (2.6.24-21-generic #1)
[156551.458539] EIP: 0060:[<c031c4a9>] EFLAGS: 00010006 CPU: 0
[156551.464209] EIP is at _spin_lock_irqsave+0x19/0x50
[156551.469170] EAX: 00000206 EBX: 3cd8500b ECX: 00000206 EDX: 3cd8500a
[156551.475624] ESI: 3cd8500a EDI: f7f26688 EBP: c041de14 ESP: c041ddfc
[156551.482077]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[156551.487657] Process swapper (pid: 0, ti=c041c000 task=c03ea3a0 task.ti=c041c000)
[156551.495084] Stack: c0136187 f7f26688 00000000 df8c1688 df8c01dc c01364d9 00000282 f7f26640 
[156551.503719]        df8c0000 f89084f5 00000001 00000082 c0125c1e c014441e f7f26640 df8c0000 
[156551.512351]        f8904568 df8c01dc f898df18 c04aef80 00000082 c01362cd 00000000 df8c0000 
[156551.521016] Call Trace:
[156551.523786]  [<c0136187>] lock_timer_base+0x27/0x60
[156551.528849]  [<c01364d9>] del_timer+0x39/0x80
[156551.533391]  [<f89084f5>] scsi_delete_timer+0x15/0x60 [scsi_mod]
[156551.539640]  [<c0125c1e>] try_to_wake_up+0x4e/0x350
[156551.544699]  [<c014441e>] ktime_get_ts+0x1e/0x60
[156551.549499]  [<f8904568>] scsi_done+0x8/0x20 [scsi_mod]
[156551.554934]  [<f898df18>] ata_scsi_qc_complete+0xa8/0x430 [libata]
[156551.561360]  [<c01362cd>] __mod_timer+0x9d/0xb0
[156551.566077]  [<f89868bc>] __ata_qc_complete+0x6c/0xe0 [libata]
[156551.572137]  [<f8909213>] scsi_run_queue+0xd3/0x1a0 [scsi_mod]
[156551.578187]  [<f898cbca>] ata_qc_complete_multiple+0x8a/0xe0 [libata]
[156551.584846]  [<f8986039>] sata_scr_write+0x59/0x70 [libata]
[156551.590652]  [<f896bc9d>] ahci_interrupt+0x7d/0x4d0 [ahci]
[156551.596370]  [<c0146bc4>] getnstimeofday+0x34/0xe0
[156551.601356]  [<c0168590>] handle_IRQ_event+0x30/0x60
[156551.606491]  [<c0169e3a>] handle_edge_irq+0xba/0x120
[156551.611645]  [<c0106f0b>] do_IRQ+0x3b/0x70
[156551.615906]  [<c01441d7>] hrtimer_start+0xc7/0x140
[156551.620902]  [<c0105403>] common_interrupt+0x23/0x30
[156551.626060]  [<c01022e6>] mwait_idle_with_hints+0x46/0x60
[156551.631669]  [<c0102695>] cpu_idle+0x45/0xd0
[156551.636114]  [<c0421a5f>] start_kernel+0x31f/0x3b0
[156551.641087]  [<c0421130>] unknown_bootoption+0x0/0x1e0
[156551.646447]  =======================
[156551.650150] Code: 26 00 ba 01 00 00 00 86 10 8b 04 24 e9 a1 5b e1 ff 90 89 c2 9c 58 0f 1f 84 00 00 00 00 00 89 c1 fa 0f 1f 84 00 00 00 00 00 90 90 <fe> 0a 79 2e f7 c1 00 02 00 00 74 1d fb 0f 1f 84 00 00 00 00 00 
[156551.670416] EIP: [<c031c4a9>] _spin_lock_irqsave+0x19/0x50 SS:ESP 0068:c041ddfc
[156551.677996] Kernel panic - not syncing: Fatal exception in interrupt

```

The machine has 4 SATA ports, each connected to a 1TB Seagate drive, and combined together in a RAID 5.

I was running a resync check on the array the last time it kernel panicked, so I am rerunning that to see if high IO load is a factor, but otherwise the only other thing I have to go on is it happens about every two days.

Does anyone have any idea what specifically could be going on to make the AHCI driver cause a kernel panic and what I can do to fix it(other than disabling AHCI)?

---

### Post by fjgaude on 2008-10-22
Some things you can try to maybe get a handle are:

```
sudo mdadm -D /dev/md0
```

or whatever your raid5 array is called.

Add this with an editor:

```
/usr/share/initramfs-tools/init   # to stop a race condition with md
   145 maybe_break mount
   146 sleep 5
   147 log_begin_msg "Mounting root file system..."

```
```
sudo /usr/sbin/update-initramfs -uk all    # run to rebuild the image
```

If you don't understand get back to us.

---

### Post by hakr89 on 2008-10-22
here's the information on the array:
```

/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Sep 26 13:32:18 2008
     Raid Level : raid5
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Oct 22 13:31:16 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 717c06d6:1b95b33b:01f9e43d:ac30fbff (local to host server)
         Events : 0.14

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

```


The root partition is on a separate IDE drive on a jmicron controller.
This setup was also stable when I was using 500GB drives and a promise SATA card previously.
Additionally, this problem doesn't occur on boot, it occurs after the system has been up for about two days.

The raid resync check completed successfully this time and didn't detect any mismatches, so the problem doesn't seem to be purely about high load or an error on one of the drives either.

---

### Post by fjgaude on 2008-10-22
Okay, but what is the "resync" command you are using?

---

### Post by hakr89 on 2008-10-23
echo check > /sys/block/md0/md/sync_action

---

### Post by fjgaude on 2008-10-23
The re-sync command is certainly valid... I wonder if you have done a **fsck** on the array with it unmounted, of course?

I can only think of a drive error, random, that is not being caught during normal use of the array. Or it could be a random error caused by hardware failure, motherboard, controller, etc. "I hate when this happens!"

Over the years I've had three power supply failures, one CPU, two motherboards, many hard drives... and here we are... not knowing what to suggest. <smile>

---

