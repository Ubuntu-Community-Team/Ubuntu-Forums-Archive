---
title: "Screen black &amp; all froozen [fglrx:drm_free] *ERROR* [driver] Excess frees:"
date: 2008-11-14
forum: General Help
---

### Post by HilliBilly on 2008-11-14
hi,

since upgrading from 7.10 to 8.04 my pc's are freezing randomly. all pc's have been rock stable on 7.04. two have been upgraded and are 'self-locking' now, the third is still on 7.10 and -as i said- rock stable.

'freezing' means that screen goes black and the pc can't be waked up anymore. i'm still able to ssh into the machines and the Xorg process takes all the %CPU 

**~$ top**
5523 root      20   0  381m  92m  18m R   99  4.6   1263:52 Xorg        

in my kern.log i found some error messages but i couldn't find any solutions neither here nor in google.

any help is very much appreciated!!!



**~$ uname -r**
2.6.24-21-generic


**~$ vi kern.log**
Nov 13 17:29:58 centurion4 kernel: [   37.164139] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 13 17:29:58 centurion4 kernel: [   37.177526] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
Nov 13 17:29:58 centurion4 kernel: [   37.177909] [fglrx] ASYNCIO init succeed!
Nov 13 17:29:58 centurion4 kernel: [   37.179215] [fglrx] PAT is enabled successfully!
Nov 13 17:29:58 centurion4 kernel: [   37.179229] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0

...

Nov 13 17:30:03 centurion4 kernel: [   46.322892] [fglrx] Reserve Block - 0 offset =  0Xfffb000 length = 0X5000
Nov 13 17:30:03 centurion4 kernel: [   46.322897] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Nov 13 17:30:03 centurion4 kernel: [   46.322899] [fglrx] Reserve Block - 2 offset =  0Xffbb000 length = 0X40000
Nov 13 17:30:03 centurion4 kernel: [   46.371250] [fglrx] interrupt source 20008000 successfully enabled
Nov 13 17:30:03 centurion4 kernel: [   46.371255] [fglrx] enable ID = 0x00000008
Nov 13 17:30:03 centurion4 kernel: [   46.371262] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Nov 13 17:30:03 centurion4 kernel: [   46.371306] [fglrx] interrupt source 10000000 successfully enabled
Nov 13 17:30:03 centurion4 kernel: [   46.371308] [fglrx] enable ID = 0x00000009
Nov 13 17:30:03 centurion4 kernel: [   46.371311] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Nov 13 17:30:04 centurion4 kernel: [   46.871331] NET: Registered protocol family 17
Nov 13 17:30:15 centurion4 kernel: [   60.290382] eth0: no IPv6 routers present
Nov 13 18:01:35 centurion4 kernel: [ 1935.205619] audit(1226595695.706:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6264 profile="/usr/sbin/cupsd" namespace="default"
Nov 13 20:14:53 centurion4 kernel: [ 9912.007674] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to enable interrupt source 20008000
Nov 13 20:14:53 centurion4 kernel: [ 9912.007680] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Nov 13 20:14:53 centurion4 kernel: [ 9912.007688] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to enable interrupt source 10000000
Nov 13 20:14:53 centurion4 kernel: [ 9912.007691] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Nov 13 20:16:55 centurion4 kernel: [10033.870557] [fglrx] interrupt source 10000000 successfully disabled!
Nov 13 20:16:55 centurion4 kernel: [10033.870562] [fglrx] enable ID = 0x00000001
Nov 13 20:16:55 centurion4 kernel: [10033.870564] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000001
Nov 13 20:16:55 centurion4 kernel: [10033.870571] [fglrx] interrupt source 20008000 successfully disabled!
Nov 13 20:16:55 centurion4 kernel: [10033.870572] [fglrx] enable ID = 0x00000002
Nov 13 20:16:55 centurion4 kernel: [10033.870574] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000002
Nov 13 20:16:57 centurion4 kernel: [10035.118054] [fglrx:firegl_lock_free] *ERROR* lock was not held by 7! (*lock=0x00000001)
Nov 13 20:16:57 centurion4 kernel: [10035.118059] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!
Nov 13 20:41:40 centurion4 kernel: [11514.072765] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483557 frees, -2147483648 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072771] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483558 frees, -2147483648 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072776] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483559 frees, -2147483646 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072778] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483560 frees, -2147483646 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072782] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483561 frees, -2147483644 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072785] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483562 frees, -2147483644 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072789] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483563 frees, -2147483642 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072792] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483564 frees, -2147483642 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072796] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483565 frees, -2147483640 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072799] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483566 frees, -2147483640 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072803] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483567 frees, -2147483638 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072806] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483568 frees, -2147483638 allocs

...

Nov 13 23:09:49 centurion4 kernel: [20379.802182] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483647 frees, -2147483558 allocs
Nov 13 23:59:07 centurion4 kernel: [23330.280791] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483557 frees, -2147483648 allocs

...

Nov 13 23:59:07 centurion4 kernel: [23330.281108] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483647 frees, -2147483558 allocs
Nov 14 00:48:30 centurion4 kernel: [26284.906632] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483557 frees, -2147483648 allocs

...

Nov 14 00:48:30 centurion4 kernel: [26284.906946] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483647 frees, -2147483558 allocs
Nov 14 01:37:52 centurion4 kernel: [29239.302660] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483557 frees, -2147483648 allocs


**it 'jumps' every 49m22s but why?!**

---

### Post by mastapat11 on 2009-10-28
> **HilliBilly said:**
> hi,

since upgrading from 7.10 to 8.04 my pc's are freezing randomly. all pc's have been rock stable on 7.04. two have been upgraded and are 'self-locking' now, the third is still on 7.10 and -as i said- rock stable.

'freezing' means that screen goes black and the pc can't be waked up anymore. i'm still able to ssh into the machines and the Xorg process takes all the %CPU 

**~$ top**
5523 root      20   0  381m  92m  18m R   99  4.6   1263:52 Xorg        

in my kern.log i found some error messages but i couldn't find any solutions neither here nor in google.

any help is very much appreciated!!!



**~$ uname -r**
2.6.24-21-generic


**~$ vi kern.log**
.
.
.
Nov 13 20:41:40 centurion4 kernel: [11514.072765] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483557 frees, -2147483648 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072771] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483558 frees, -2147483648 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072776] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483559 frees, -2147483646 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072778] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483560 frees, -2147483646 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072782] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483561 frees, -2147483644 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072785] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483562 frees, -2147483644 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072789] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483563 frees, -2147483642 allocs
Nov 13 20:41:40 centurion4 kernel: [11514.072792] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483564 frees, -2147483642 allocs
.
.
.


I have this same issue.  I bet it has something to do with the fglrx driver.
i'm gonna try the ati driver and see how it goes. I'm tired of my machine dying on me EVERY couple of days!

p@G:~$ uname -a
Linux G 2.6.24-25-generic #1 SMP Tue Oct 20 06:49:12 UTC 2009 x86_64 GNU/Linux

Anybody out there got any tips? tnx!
Hardy x64, ATI Radeon HD3650

---

