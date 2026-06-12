---
title: "SAS HBA not detected"
date: 2023-01-23
forum: Hardware
---

### Post by heavyarms2112 on 2023-01-23
I have a Netapp X2069 SAS HBA card (pcie 3.0) and trying to access drives to my disk shelf.
```
10:00.0 Serial Attached SCSI controller: PMC-Sierra Inc. PM8072 Tachyon SPCv 12G 16-port SAS/SATA controller (rev 06)
```
This one doesn't get detected on Ubuntu. kernel driver isn't loaded and manual load of pm80xx doesn't show up anything. Nothing in dmesg either.

From the source it seems like this card should've worked with the same pm80xx driver?
[https://github.com/torvalds/linux/blob/master/drivers/scsi/pm8001/pm8001_init.c#L1499](https://github.com/torvalds/linux/blob/master/drivers/scsi/pm8001/pm8001_init.c#L1499)

The card is detected fine on FreeBSD. disks are seen, shelf is seen, IO test ran. It seems it's using the below driver.
[https://www.freebsd.org/cgi/man.cgi?query=pmspcv&manpath=FreeBSD+11.0-RELEASE+and+Ports](https://www.freebsd.org/cgi/man.cgi?query=pmspcv&manpath=FreeBSD+11.0-RELEASE+and+Ports)

Now, the pcie 2.0 version of this card, Netapp X2065A which is based on PM8003 chipset and that works with pm80xx on Ubuntu, disk shelf, all drives and IO tests worked.

Ubuntu 20.04.5, Kernel 5.18.x
Note: Tried 5.4.x as well.

Basically don't have a working driver for Ubuntu for this card.

---

### Post by alexey-9 on 2023-02-03
> **heavyarms2112 said:**
> I have a Netapp X2069 SAS HBA card (pcie 3.0) and trying to access drives to my disk shelf.
From the source it seems like this card should've worked with the same pm80xx driver?
[https://github.com/torvalds/linux/blob/master/drivers/scsi/pm8001/pm8001_init.c#L1499](https://github.com/torvalds/linux/blob/master/drivers/scsi/pm8001/pm8001_init.c#L1499)



PCI_VENDOR_ID_ATTO is 0x117c
Your card has vendor id 0x11f8 (PMC_Sierra)
It is weird, but no combination of PMC_Sierra and 0x8072 chip exists in the driver.
May be you can try to define it.

Update:
It does not work. I have compiled custom kernel module for pm80xx, including PMC_Sierra with chipid 0x8072

> 
pm80xx0:: mpi_uninit_check  1528:TIMEOUT:IBDB value/=2
pm80xx0:: pm80xx_chip_soft_rst  1609:MPI state is not ready scratch: 40002000:2a0e:1000:33001000
pm80xx0:: mpi_init_check  1011:Inb doorbell clear not toggled[value:1]
pm80xx0:: pm8001_pci_probe  1118:chip_init failed [ret: -16]
pm80xx: probe of 0000:0a:00.0 failed with error -16


Even worse with init patched to match those of ATTO
> 
 pm80xx 0000:0a:00.0: pm80xx: driver version 0.1.40 :: pm8001_pci_alloc  527:Setting link rate to default value
 ------------[ cut here ]------------
 WARNING: CPU: 0 PID: 1855463 at drivers/pci/msi.c:1064 pci_alloc_irq_vectors_affinity+0x204/0x230
 Modules linked in: pm80xx(+) rpcsec_gss_krb5 veth ebtable_filter ebtables ip_set ip6table_raw iptable_raw ip6table_filter ip6_tables iptable_filter bpfilter nf_tables 8021q garp mrp bonding tls softdog nfnetlink_log nfnetlink ipmi_ssif intel_rapl_msr intel_rapl_common sb_edac x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul mgag200 ghash_clmulni_intel aesni_intel drm_kms_helper cec crypto_simd rc_core cryptd fb_sys_fops rapl syscopyarea sysfillrect intel_cstate sysimgblt pcspkr joydev input_leds mei_me mei mxm_wmi acpi_ipmi ipmi_si ipmi_devintf ipmi_msghandler mac_hid acpi_pad acpi_power_meter zfs(PO) zunicode(PO) zzstd(O) zlua(O) zavl(PO) icp(PO) zcommon(PO) znvpair(PO) spl(O) vhost_net vhost vhost_iotlb tap ib_iser rdma_cm iw_cm ib_cm ib_core nfsd iscsi_tcp libiscsi_tcp auth_rpcgss libiscsi nfs_acl scsi_transport_iscsi lockd grace drm sunrpc ip_tables x_tables autofs4 btrfs blake2b_generic xor zstd_compress raid6_pq simplefb
  dm_thin_pool dm_persistent_data dm_bio_prison dm_bufio libcrc32c ses enclosure hid_generic usbmouse usbkbd usbhid hid crc32_pclmul fnic libfcoe ahci igb libfc ehci_pci i2c_algo_bit libahci lpc_ich dca scsi_transport_fc libsas ehci_hcd enic megaraid_sas scsi_transport_sas wmi [last unloaded: pm80xx]
 CPU: 0 PID: 1855463 Comm: kworker/0:2 Tainted: P           O      5.15.85-1-pve #1
 Hardware name: Cisco Systems Inc UCSC-C240-M4SX/UCSC-C240-M4SX, BIOS C240M4.4.1.2c.0.0202211902 02/02/2021
 Workqueue: events work_for_cpu_fn
 RIP: 0010:pci_alloc_irq_vectors_affinity+0x204/0x230
 Code: 4d 85 f6 74 0d 4c 89 f6 bf 01 00 00 00 e8 04 32 a7 ff be 01 00 00 00 4c 89 ff 41 bc 01 00 00 00 e8 f1 d2 fe ff e9 70 fe ff ff <0f> 0b 41 bc ea ff ff ff e9 4a fe ff ff 41 bc de ff ff ff e9 3f fe
 RSP: 0018:ffffa5da085e7cb8 EFLAGS: 00010202
 RAX: 0000000000000028 RBX: 0000000000000028 RCX: 0000000000000000
 RDX: ffffa5da085e7cc8 RSI: 0000000000000028 RDI: ffffa5da085e7cf8
 RBP: ffffa5da085e7d28 R08: 0000000000000000 R09: 0000000000000040
 R10: 000000000000ffff R11: 0000000000000000 R12: ffff9801be1f0000
 R13: 0000000000000004 R14: 0000000000000000 R15: ffff97fd45944000
 FS:  0000000000000000(0000) GS:ffff980c7fc00000(0000) knlGS:0000000000000000
 CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
 CR2: 0000557fee0dbb18 CR3: 0000001f16e10005 CR4: 00000000001726f0
 Call Trace:
  <TASK>
  pm8001_pci_probe+0x7cf/0x1b97 [pm80xx]
  ? finish_task_switch.isra.0+0x7e/0x2b0
  local_pci_probe+0x4b/0x90
  work_for_cpu_fn+0x1a/0x30
  process_one_work+0x22b/0x3d0
  worker_thread+0x223/0x420
  ? process_one_work+0x3d0/0x3d0
  kthread+0x12a/0x150
  ? set_kthread_struct+0x50/0x50
  ret_from_fork+0x22/0x30
  </TASK>
 ---[ end trace 1e106d7104d78503 ]---
pm80xx0:: pm8001_alloc  282:pm8001_setup_irq failed [ret: -22]
pm80xx: probe of 0000:0a:00.0 failed with error -12


So someone competent should check FreeBSD driver and adapt Linux one for this card.

---

### Post by heavyarms2112 on 2023-02-27
Thanks for response. Yes, this is exactly the issue. The pci vendor id combo isn't present.
I was messing with kernel source and had managed to get it working. But I broke it again and now I don't know what hacks I had used :D

>  { PCI_VDEVICE(PMC_Sierra, 0x8072), chip_8072 },

Just adding that makes the driver load.
> pm8001_mpi_get_nvmd_resp 3054: Get nvm data error 1

---

