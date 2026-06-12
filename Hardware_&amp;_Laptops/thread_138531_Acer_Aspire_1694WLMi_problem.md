---
title: "Acer Aspire 1694WLMi problem"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by pestilence on 2006-03-02
OK here is the situation, i have 2.6.15 +ck compiled and installed my problem is that when the system boots i get the following entry in my logs:
```

[fglrx] module loaded - fglrx 8.22.5 [Feb  7 2006] on minor 0
[fglrx] free  PCIe = 51118080
[fglrx] max   PCIe = 51118080
[fglrx] free  LFB = 119762944
[fglrx] max   LFB = 119762944
[fglrx] free  Inv = 134217728
[fglrx] max   Inv = 134217728
[fglrx] total Inv = 134217728
[fglrx] total TIM = 0[fglrx] total FB  = 0
[fglrx] total PCIe = 16384
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: status error: status=0x51 { DriveReady SeekComplete Error }
hdb: status error: error=0x04 { AbortedCommand }
ide: failed opcode was: unknown
hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: drive not ready for command
hda: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: status error: status=0x51 { DriveReady SeekComplete Error }
hdb: status error: error=0x04 { AbortedCommand }
ide: failed opcode was: unknown
hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: drive not ready for command
hda: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: status error: status=0x51 { DriveReady SeekComplete Error }
hdb: status error: error=0x04 { AbortedCommand }
ide: failed opcode was: unknown
hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: drive not ready for command
hda: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: drive not ready for command
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdb: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown

```

My hdparm.conf settings:
```

command_line {
       hdparm -d1 -m 16 -c3 /dev/hda
}

command_line {
       hdparm -d1 /dev/hdb
}

```

I have **used many other different configs but i always hit the same errors**
Check if hdparms settings are set:
```

pestilence@odin:/lib/modules/2.6.15-pestilence-2b$ sudo hdparm -v /dev/hda

/dev/hda:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 195371568, start = 0

```

And for hdb (DVD drive):
```

pestilence@odin:/lib/modules/2.6.15-pestilence-2b$ sudo hdparm -v /dev/hdb

/dev/hdb:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

I am experiencing a few problems that i think they are related to this issue:
1) When i logout from my KDE session to drop to a shell i get lots of times (**not always**) a **black screen** (system **is** responding, it does not freeze but i can't see anything on the console).
I had vesafb compiled inside the kernel and it was present in my grub conf:
**video=vesafb** i disabled the option and i left **only** the vga=791 entry to have a nicer booting procedure.
Sometimes when i am able to access the console i see the following error:
```

modprobe: FATAL: Could not load /lib/modules/2.6.15-pestilence-2b/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.15-pestilence-2b/modules.dep: No such file or directory

Loading, please wait...
insmod: error inserting '/lib/modules/2.6.15-pestilence-2b/kernel/drivers/video/console/bitblit.ko': -1 Unknown symbol in module
insmod: can't read '/lib/modules/2.6.15-pestilence-2b/kernel/drivers/video/console/tileblit.ko': No such file or directory
insmod: error inserting '/lib/modules/2.6.15-pestilence-2b/kernel/drivers/video/console/fbcon.ko': -1 Unknown symbol in module
insmod: can't read '/lib/modules/2.6.15-pestilence-2b/kernel/drivers/video/cfbcopyarea.ko': No such file or directory
insmod: can't read '/lib/modules/2.6.15-pestilence-2b/kernel/drivers/video/cfbfillrect.ko': No such file or directory
insmod: can't read '/lib/modules/2.6.15-pestilence-2b/kernel/drivers/video/cfbimgblt.ko': No such file or directory
insmod: can't read '/lib/modules/2.6.15-pestilence-2b/kernel/drivers/video/softcursor.ko': No such file or directory
insmod: can't read '/lib/modules/2.6.15-pestilence-2b/kernel/drivers/video/vesafb.ko': No such file or directory
FATAL: Module ext3 not found.

```

Off course this is not the case since:
```

pestilence@odin:~$ ls -al /lib/modules/2.6.15-pestilence-2b/modules.dep
-rw-r--r--  1 root root 7632 2006-02-27 02:05 /lib/modules/2.6.15-pestilence-2b/modules.dep

```

Plus all the other mentioned files are there.
Now i am thinking of this as a problem related to the hdparm messages, my laptop is brand new (less than a month) and currently i am running a read test on my HD (**sudo dd if=/dev/hda of=/dev/null bs=64k**)
But up to now i see no problems reported.
Anyone else having a clue?

---

### Post by pestilence on 2006-03-02
OK more info.
I disabled hdparm settings for hda in /etc/hdparm.conf:
```

#command_line {
#       hdparm -d1 -m 16 -c3 -X66 /dev/hda
#}

command_line {
       hdparm -d1 /dev/hdb
}

```
And the errors stopped appearing inside my logs, i initialy supposed that this would disable DMA etc on my hda but a test prooved me wrong:
```

pestilence@odin:~$ sudo hdparm -v /dev/hda

/dev/hda:
 multcount    = 16 (on)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 195371568, start = 0

```
I guess this has to do with the AUTODMA kernel option (forgot that i included it).

Regardless the error dissapearing i am still experiencing the **modules.dep** errors above.
This is reproduced everytime i try to do a console login from KDM if i try a **CTRL+ALT+F1** login the error does not appear!?

---

