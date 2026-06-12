---
title: "Segfault with UVC webcam"
date: 2016-04-10
forum: Hardware
---

### Post by cpdondo on 2016-04-10
I am trying to use a Samsung branded webcam and it's resulting in a segfault.  This happens with both 3.13 and 4.3.6 kernels.  Googling around doesn't reveal anything useful.

The camera is recognized when plugged in, but segfaults on access.  Tested with cheese and vlc.

```
[  110.605327] usb 2-1.2: new high-speed USB device number 5 using ehci-pci
[  110.698450] usb 2-1.2: New USB device found, idVendor=04e8, idProduct=2061
[  110.698458] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  110.698462] usb 2-1.2: Product: USB2.0 UVC HQ WebCam
[  110.698465] usb 2-1.2: Manufacturer: Alpha Imaging Tech. Corp.
[  110.698889] uvcvideo: Found UVC 1.00 device USB2.0 UVC HQ WebCam (04e8:2061)
[  110.699547] input: USB2.0 UVC HQ WebCam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input16
[  136.030151] vmalloc: allocation failure: 0 bytes
[  136.030156] video_source:sr: page allocation failure: order:0, mode:0x80d2
[  136.030160] CPU: 3 PID: 10533 Comm: video_source:sr Not tainted 4.3.6-040306-generic #201602191831
[  136.030162] Hardware name: LENOVO 243852U/243852U, BIOS G5ET98WW (2.58 ) 04/01/2014
[  136.030164]  0000000000000000 000000005823f19b ffff8805a5ee3a20 ffffffff813c2e44
[  136.030167]  00000000000080d2 ffff8805a5ee3ab0 ffffffff8118a4d7 ffffffff81acc738
[  136.030170]  ffff8805a5ee3a40 ffff880500000018 ffff8805a5ee3ac0 ffff8805a5ee3a60
[  136.030173] Call Trace:
[  136.030181]  [<ffffffff813c2e44>] dump_stack+0x44/0x60
[  136.030187]  [<ffffffff8118a4d7>] warn_alloc_failed+0xf7/0x150
[  136.030193]  [<ffffffff815de2eb>] ? usb_start_wait_urb+0xab/0x170
[  136.030196]  [<ffffffff815de49b>] ? usb_control_msg+0xeb/0x130
[  136.030200]  [<ffffffff811c526b>] __vmalloc_node_range+0x20b/0x290
[  136.030203]  [<ffffffff815de49b>] ? usb_control_msg+0xeb/0x130
[  136.030205]  [<ffffffff811c54b5>] vmalloc_user+0x55/0x90
[  136.030211]  [<ffffffffc05026e6>] ? vb2_vmalloc_alloc+0x46/0xc0 [videobuf2_vmalloc]
[  136.030214]  [<ffffffffc05026e6>] vb2_vmalloc_alloc+0x46/0xc0 [videobuf2_vmalloc]
[  136.030220]  [<ffffffffc06e7a44>] __vb2_queue_alloc+0x164/0x530 [videobuf2_core]
[  136.030224]  [<ffffffffc06e8008>] __reqbufs.isra.20+0x1f8/0x360 [videobuf2_core]
[  136.030228]  [<ffffffffc06e81a0>] vb2_reqbufs+0x30/0x40 [videobuf2_core]
[  136.030232]  [<ffffffffc073759e>] uvc_request_buffers+0x2e/0x50 [uvcvideo]
[  136.030236]  [<ffffffffc073969a>] uvc_ioctl_reqbufs+0x4a/0xa0 [uvcvideo]
[  136.030244]  [<ffffffffc049b503>] v4l_reqbufs+0x43/0x50 [videodev]
[  136.030249]  [<ffffffffc049a101>] __video_do_ioctl+0x291/0x310 [videodev]
[  136.030256]  [<ffffffffc0499c3e>] video_usercopy+0x33e/0x550 [videodev]
[  136.030261]  [<ffffffffc0499e70>] ? video_ioctl2+0x20/0x20 [videodev]
[  136.030265]  [<ffffffff816c8135>] ? sock_write_iter+0x85/0xf0
[  136.030271]  [<ffffffffc0499e65>] video_ioctl2+0x15/0x20 [videodev]
[  136.030276]  [<ffffffffc04956a3>] v4l2_ioctl+0xd3/0xe0 [videodev]
[  136.030280]  [<ffffffff81214ff5>] do_vfs_ioctl+0x295/0x480
[  136.030284]  [<ffffffff81201d76>] ? vfs_write+0x146/0x1a0
[  136.030287]  [<ffffffff81215259>] SyS_ioctl+0x79/0x90
[  136.030290]  [<ffffffff817ec7b6>] entry_SYSCALL_64_fastpath+0x16/0x75
[  136.030292] Mem-Info:
[  136.030297] active_anon:321167 inactive_anon:28083 isolated_anon:0
[  136.030297]  active_file:69108 inactive_file:202742 isolated_file:0
[  136.030297]  unevictable:27 dirty:119 writeback:0 unstable:0
[  136.030297]  slab_reclaimable:11597 slab_unreclaimable:9590
[  136.030297]  mapped:62552 shmem:28410 pagetables:9020 bounce:0
[  136.030297]  free:5376384 free_pcp:2637 free_cma:0
[  136.030302] Node 0 DMA free:15884kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15984kB managed:15900kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:16kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[  136.030308] lowmem_reserve[]: 0 2550 23648 23648
[  136.030311] Node 0 DMA32 free:2224980kB min:2116kB low:2644kB high:3172kB active_anon:222304kB inactive_anon:13472kB active_file:31616kB inactive_file:97440kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2693612kB managed:2613408kB mlocked:0kB dirty:36kB writeback:0kB mapped:28924kB shmem:13592kB slab_reclaimable:4936kB slab_unreclaimable:3792kB kernel_stack:992kB pagetables:4044kB unstable:0kB bounce:0kB free_pcp:5472kB local_pcp:696kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[  136.030317] lowmem_reserve[]: 0 0 21098 21098
[  136.030320] Node 0 Normal free:19264672kB min:17516kB low:21892kB high:26272kB active_anon:1062364kB inactive_anon:98860kB active_file:244816kB inactive_file:713528kB unevictable:108kB isolated(anon):0kB isolated(file):0kB present:21993472kB managed:21604496kB mlocked:108kB dirty:440kB writeback:0kB mapped:221284kB shmem:100048kB slab_reclaimable:41452kB slab_unreclaimable:34552kB kernel_stack:8240kB pagetables:32036kB unstable:0kB bounce:0kB free_pcp:5076kB local_pcp:632kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[  136.030326] lowmem_reserve[]: 0 0 0 0
[  136.030329] Node 0 DMA: 1*4kB (U) 1*8kB (U) 2*16kB (U) 1*32kB (U) 1*64kB (U) 1*128kB (U) 1*256kB (U) 0*512kB 1*1024kB (U) 1*2048kB (M) 3*4096kB (M) = 15884kB
[  136.030341] Node 0 DMA32: 268*4kB (UEM) 71*8kB (UEM) 25*16kB (UEM) 8*32kB (UEM) 4*64kB (UEM) 3*128kB (UM) 0*256kB 4*512kB (UEM) 0*1024kB 2*2048kB (EM) 541*4096kB (M) = 2225016kB
[  136.030352] Node 0 Normal: 469*4kB (UEM) 253*8kB (UEM) 122*16kB (UEM) 39*32kB (UEM) 21*64kB (UEM) 8*128kB (UM) 1*256kB (U) 2*512kB (UE) 1*1024kB (M) 1*2048kB (E) 4700*4096kB (M) = 19265020kB
[  136.030366] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
[  136.030367] 300262 total pagecache pages
[  136.030369] 0 pages in swap cache
[  136.030370] Swap cache stats: add 0, delete 0, find 0/0
[  136.030371] Free swap  = 15624188kB
[  136.030372] Total swap = 15624188kB
[  136.030374] 6175767 pages RAM
[  136.030375] 0 pages HighMem/MovableOnly
[  136.030376] 117316 pages reserved
[  136.030377] 0 pages cma reserved
[  136.030378] 0 pages hwpoisoned
[  136.293238] vmalloc: allocation failure: 0 bytes
[  136.293240] video_source:sr: page allocation failure: order:0, mode:0x80d2
[  136.293242] CPU: 3 PID: 10533 Comm: video_source:sr Not tainted 4.3.6-040306-generic #201602191831
[  136.293243] Hardware name: LENOVO 243852U/243852U, BIOS G5ET98WW (2.58 ) 04/01/2014
[  136.293244]  0000000000000000 000000005823f19b ffff8805a5ee3a20 ffffffff813c2e44
[  136.293246]  00000000000080d2 ffff8805a5ee3ab0 ffffffff8118a4d7 ffffffff81acc738
[  136.293247]  ffff8805a5ee3a40 ffff880500000018 ffff8805a5ee3ac0 ffff8805a5ee3a60
[  136.293248] Call Trace:
[  136.293255]  [<ffffffff813c2e44>] dump_stack+0x44/0x60
[  136.293258]  [<ffffffff8118a4d7>] warn_alloc_failed+0xf7/0x150
[  136.293260]  [<ffffffff811c526b>] __vmalloc_node_range+0x20b/0x290
[  136.293262]  [<ffffffff811c54b5>] vmalloc_user+0x55/0x90
[  136.293265]  [<ffffffffc05026e6>] ? vb2_vmalloc_alloc+0x46/0xc0 [videobuf2_vmalloc]
[  136.293267]  [<ffffffffc05026e6>] vb2_vmalloc_alloc+0x46/0xc0 [videobuf2_vmalloc]
[  136.293270]  [<ffffffffc06e7a44>] __vb2_queue_alloc+0x164/0x530 [videobuf2_core]
[  136.293272]  [<ffffffffc06e8008>] __reqbufs.isra.20+0x1f8/0x360 [videobuf2_core]
[  136.293274]  [<ffffffffc06e81a0>] vb2_reqbufs+0x30/0x40 [videobuf2_core]
[  136.293276]  [<ffffffffc073759e>] uvc_request_buffers+0x2e/0x50 [uvcvideo]
[  136.293278]  [<ffffffffc073969a>] uvc_ioctl_reqbufs+0x4a/0xa0 [uvcvideo]
[  136.293283]  [<ffffffffc049b503>] v4l_reqbufs+0x43/0x50 [videodev]
[  136.293286]  [<ffffffffc049a101>] __video_do_ioctl+0x291/0x310 [videodev]
[  136.293289]  [<ffffffffc0499c3e>] video_usercopy+0x33e/0x550 [videodev]
[  136.293291]  [<ffffffffc0499e70>] ? video_ioctl2+0x20/0x20 [videodev]
[  136.293294]  [<ffffffff810f9e50>] ? futex_wake+0x90/0x170
[  136.293297]  [<ffffffffc0499e65>] video_ioctl2+0x15/0x20 [videodev]
[  136.293299]  [<ffffffffc04956a3>] v4l2_ioctl+0xd3/0xe0 [videodev]
[  136.293301]  [<ffffffff81214ff5>] do_vfs_ioctl+0x295/0x480
[  136.293302]  [<ffffffff81215259>] SyS_ioctl+0x79/0x90
[  136.293304]  [<ffffffff817ec7b6>] entry_SYSCALL_64_fastpath+0x16/0x75
[  136.293305] Mem-Info:
[  136.293308] active_anon:321094 inactive_anon:28083 isolated_anon:0
[  136.293308]  active_file:69108 inactive_file:202742 isolated_file:0
[  136.293308]  unevictable:27 dirty:119 writeback:0 unstable:0
[  136.293308]  slab_reclaimable:11597 slab_unreclaimable:9590
[  136.293308]  mapped:62552 shmem:28410 pagetables:9020 bounce:0
[  136.293308]  free:5376457 free_pcp:2623 free_cma:0
[  136.293310] Node 0 DMA free:15884kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15984kB managed:15900kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:16kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[  136.293314] lowmem_reserve[]: 0 2550 23648 23648
[  136.293315] Node 0 DMA32 free:2224980kB min:2116kB low:2644kB high:3172kB active_anon:222304kB inactive_anon:13472kB active_file:31616kB inactive_file:97440kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2693612kB managed:2613408kB mlocked:0kB dirty:36kB writeback:0kB mapped:28924kB shmem:13592kB slab_reclaimable:4936kB slab_unreclaimable:3792kB kernel_stack:992kB pagetables:4044kB unstable:0kB bounce:0kB free_pcp:5472kB local_pcp:696kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[  136.293318] lowmem_reserve[]: 0 0 21098 21098
[  136.293320] Node 0 Normal free:19264964kB min:17516kB low:21892kB high:26272kB active_anon:1062072kB inactive_anon:98860kB active_file:244816kB inactive_file:713528kB unevictable:108kB isolated(anon):0kB isolated(file):0kB present:21993472kB managed:21604496kB mlocked:108kB dirty:440kB writeback:0kB mapped:221284kB shmem:100048kB slab_reclaimable:41452kB slab_unreclaimable:34552kB kernel_stack:8240kB pagetables:32036kB unstable:0kB bounce:0kB free_pcp:5020kB local_pcp:652kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[  136.293323] lowmem_reserve[]: 0 0 0 0
[  136.293324] Node 0 DMA: 1*4kB (U) 1*8kB (U) 2*16kB (U) 1*32kB (U) 1*64kB (U) 1*128kB (U) 1*256kB (U) 0*512kB 1*1024kB (U) 1*2048kB (M) 3*4096kB (M) = 15884kB
[  136.293331] Node 0 DMA32: 268*4kB (UEM) 71*8kB (UEM) 25*16kB (UEM) 8*32kB (UEM) 4*64kB (UEM) 3*128kB (UM) 0*256kB 4*512kB (UEM) 0*1024kB 2*2048kB (EM) 541*4096kB (M) = 2225016kB
[  136.293337] Node 0 Normal: 488*4kB (UEM) 252*8kB (UEM) 129*16kB (UEM) 45*32kB (UEM) 21*64kB (UEM) 8*128kB (UM) 1*256kB (U) 2*512kB (UE) 1*1024kB (M) 1*2048kB (E) 4700*4096kB (M) = 19265392kB
[  136.293344] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
[  136.293345] 300262 total pagecache pages
[  136.293346] 0 pages in swap cache
[  136.293347] Swap cache stats: add 0, delete 0, find 0/0
[  136.293347] Free swap  = 15624188kB
[  136.293348] Total swap = 15624188kB
[  136.293348] 6175767 pages RAM
[  136.293349] 0 pages HighMem/MovableOnly
[  136.293350] 117316 pages reserved
[  136.293350] 0 pages cma reserved
[  136.293351] 0 pages hwpoisoned
yan@yan-ThinkPad-W530:~$ ^C
yan@yan-ThinkPad-W530:~$
```

---

### Post by MartyBuntu on 2016-04-10
Have you tried accessing the camera with **guvcview**? It's in the repo's.
It's worked for me where Cheese has failed.

---

### Post by bcschmerker on 2016-04-10
After reading the DMesg excerpt, it appears that we have a Kernel Oops involving videobuf2_core, videodev, and uvcvideo.  The LinUX Kernel Project BugZilla has a [s][Bug 42608](https://bugzilla.kernel.org/show_bug.cgi?id=42608)[/s] on file for Kernel 3.2.1 for an allocation failure preventing loading of a wireless-network driver; and Ceph Projects has a [s][Bug 13712](http://tracker.ceph.com/issues/13712)[/s] on file for Kernel 4.2.3 for a driver/module conflict involving AppArmor and RBD:  Both are similar in nature.  @cpdondo What OS release your system?

---

### Post by cpdondo on 2016-04-11
> **bcschmerker said:**
> @cpdondo What OS release your system?

14.04LTS, this happens on both 32 and 64 bit versions.  Also happens when I use USB3 or USB2 ports.

And yes, I've tried guvcview; same result.  It's a kernel oops on vmalloc: vmalloc: allocation failure: 0 bytes

My guess is that the camera reports garbage for the image size/depth and the driver then OOPSes trying to fill the request.

---

### Post by bcschmerker on 2016-04-12
After checking [/uvc/](http://www.ideasonboard.org/uvc/) at [Ideas on Board](http://www.ideasonboard.org/), I have no joy for *any* device(s) for Manufacturer Code 0x04e8 from  [Alpha Imaging Technologies Corporation](https://www.alphaimaging.com/), supported or not.  The closest Manufacturer codes are 0x04da for Matsusita-Kotobuki Electronics Industries Ltd. and 0x04f2 for Chicony Electronics Company Ltd.

---

