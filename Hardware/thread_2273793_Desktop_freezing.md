---
title: "Desktop freezing"
date: 2015-04-15
forum: Hardware
---

### Post by cody1233 on 2015-04-15
Hello, everyone!  I already posted in General Help, but maybe this is  the best place for it.  My desktop has been randomly crashing lately.  Specifically after I ran a dist-upgrade.  It starts up fine and runs for  about 2 hours, but then the desktop freezes.  Music will still play, my  files are still accessible, and I can move the mouse, but the desktop  and windows are frozen.  I have an AMD Radeon R9 270X and an AMD  FX-Series processor.  This is from the crash log:

ProblemType: KernelOops
Annotation: Your system might become unstable now and might need to be restarted.
Date: Mon Apr 13 21:35:12 2015
Failure: oops
OopsText:
 ------------[ cut here ]------------
 kernel BUG at /build/buildd/linux-3.13.0/drivers/gpu/drm/radeon/radeon_sa.c:322!
 invalid opcode: 0000 [#1] SMP
 Modules linked in: btrfs(X) raid6_pq(X) xor(X) ufs(X) qnx4(X)   hfsplus(X) hfs(X) minix(X) ntfs(X) msdos(X) jfs(X) xfs(X) libcrc32c(X)   pci_s$
 CPU: 3 PID: 1722 Comm: gnome-shell Tainted: G           OX 3.13.0-49-generic #81-Ubuntu
 Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./970A-D3P, BIOS F5 08/06/2013
 task: ffff880231933000 ti: ffff880232590000 task.ti: ffff880232590000
 RIP: 0010:[<ffffffffa0173efd>]  [<ffffffffa0173efd>] radeon_sa_bo_new+0x49d/0x4c0 [radeon]
 RSP: 0018:ffff8802325919f8  EFLAGS: 00010287
 RAX: 0000000000102d10 RBX: ffff88022da59330 RCX: 0000000000102d10
 RDX: ffff880232591b68 RSI: ffff88022da59330 RDI: ffff88022da58000
 RBP: ffff880232591ad8 R08: 0000000000000100 R09: 0000000000000001
 R10: 0000000000000000 R11: ffffffffa0173455 R12: ffff88022da58000
 R13: 0000000000000000 R14: 0000000000000003 R15: ffff880035ab5080
 FS:  00007fbaa9517700(0000) GS:ffff88023ed80000(0000) knlGS:00000000eceffb40
 CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
 CR2: 00007fba56a00000 CR3: 0000000231d63000 CR4: 00000000000407e0
 Stack:
  000000000000000b ffff88022da58e38 ffff88022da58000 ffff880232591b68
  00102d1001591a70 ffffffffa01120d5 0000000000000100 0000000000000498
  0000000100000000 0000000000000000 ffff8802245fafa0 00000000001ab128
 Call Trace:
  [<ffffffffa01120d5>] ? radeon_fence_process+0xe5/0x130 [radeon]
  [<ffffffffa0128c19>] radeon_ib_get+0x39/0xe0 [radeon]
  [<ffffffffa0116b31>] radeon_vm_bo_update+0x101/0x680 [radeon]
  [<ffffffffa0083c2d>] ? ttm_eu_list_ref_sub+0x3d/0x60 [ttm]
  [<ffffffffa0178800>] ? si_ib_parse+0x280/0x460 [radeon]
  [<ffffffffa012b6da>] radeon_cs_ioctl+0x90a/0xa20 [radeon]
  [<ffffffffa0003c22>] drm_ioctl+0x502/0x630 [drm]
  [<ffffffff810d91b1>] ? futex_wake+0x1b1/0x1d0
  [<ffffffffa00de0fe>] radeon_drm_ioctl+0x4e/0x90 [radeon]
  [<ffffffff811d1200>] do_vfs_ioctl+0x2e0/0x4c0
  [<ffffffff811d1461>] SyS_ioctl+0x81/0xa0
  [<ffffffff8173263d>] system_call_fastpath+0x1a/0x1f
 Code: e1 48 8b 9d 38 ff ff ff 48 8b 3b e8 7e e4 02 e1 48 c7 03 00 00 00   00 44 89 e8 e9 0d fd ff ff b8 f4 ff ff ff e9 03 fd ff ff 0f 0b <0f$
 RIP  [<ffffffffa0173efd>] radeon_sa_bo_new+0x49d/0x4c0 [radeon]
  RSP <ffff8802325919f8>
 ---[ end trace e12574b1956b16f3 ]---

Here is some interesting output from kernel log: 

[ 6337.714189] ------------[ cut here ]------------
[ 6337.714214] kernel BUG at /build/buildd/linux-3.13.0/drivers/gpu/drm/radeon/radeon_sa.c:322!
[ 6337.714249] invalid opcode: 0000 [#1] SMP 
[ 6337.714268] Modules linked in: pci_stub vboxpci(OX) vboxnetadp(OX)   vboxnetflt(OX) vboxdrv(OX) rfcomm bnep bluetooth binfmt_misc dm_crypt   kvm_amd kvm snd_hda_codec_hdmi crct10dif_pclmul joydev crc32_pclmul   ghash_clmulni_intel aesn

And here is my lspci;

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port E)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao XT [Radeon R9 270X]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

I am wondering if I should file a bug report or if anybody else is  having this problem.  I would go to the fglrx drivers, but their  preformance is unacceptable.  If you need any more commands run or if  anybody can think of anything for me to try, I would be happy to try  it!!

Thanks!

---

### Post by Vladlenin5000 on 2015-04-15
Please don't open multiple threads for the same issue. It dilutes the community efforts.

---

### Post by slickymaster on 2015-04-15
Closed. Duplicate [here]("http://ubuntuforums.org/showthread.php?t=2273528").

Please do not create duplicate threads, it dilutes the community’s efforts to provide support and causes confusion.

---

