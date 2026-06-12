---
title: "Ubuntu Server 18.04 graphics in console is extremely slow"
date: 2018-08-31
forum: Hardware
---

### Post by jan.hana on 2018-08-31
Hello,
  I've just installed Ubuntu 18.04.1 to a server with Supermicro  Motherboard X11SSH-TF with Graphics Aspeed AST2400 BMC build in and  during boot up graphics get slow.

[I've recorded video example]("https://youtu.be/6Rnqq61tECk").

  During boot up is changed resolution (not possible to calibrate lcd)  and everything is slowed down. LCD is connected with VGA cable (no other  connector on motherboard).
  When I tried to install Aspeed driver, this message is returned:

```
Can't find proper X Window Version, Please update driver manually!!
```

  Also Ubuntu Server installer was "bigger" than the screen.
  Any idea?

lshw:
```

           *-pci
                description: PCI bridge
                product: AST1150 PCI-to-PCI Bridge
                vendor: ASPEED Technology, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                resources: ioport:e000(size=4096) memory:de000000-df0fffff
              *-display
                   description: VGA compatible controller
                   product: ASPEED Graphics Family
                   vendor: ASPEED Technology, Inc.
                   physical id: 0
                   bus info: pci@0000:03:00.0
                   version: 30
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm msi vga_controller bus_master cap_list rom
                   configuration: driver=ast latency=0
                   resources: irq:18 memory:de000000-deffffff memory:df000000-df01ffff ioport:e000(size=128) memory:c0000-dffff

```


dmesg:
```

[    9.593618] ata2.00: Enabling discard_zeroes_data
[   11.182667] AVX2 version of gcm_enc/dec engaged.
[   11.182667] AES CTR mode by8 optimization enabled
[   12.141034]  sdb: sdb1
[   12.141037]  sda: sda1
[   12.141177] ata1.00: Enabling discard_zeroes_data
[   12.144946] sd 0:0:0:0: [sda] supports TCG Opal
[   12.144948] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.501827] ata2.00: Enabling discard_zeroes_data
[   12.576187] sd 1:0:0:0: [sdb] supports TCG Opal
[   12.644806] sd 1:0:0:0: [sdb] Attached SCSI disk
[   12.712732] dca service started, version 1.12.1
[   12.784242] ixgbe: Intel(R) 10 Gigabit PCI Express Network Driver - version 5.1.0-k
[   12.784676] [drm] Using P2A bridge for configuration
[   12.784687] [drm] AST 2400 detected
[   12.784777] [drm] Analog VGA only
[   12.784890] [drm] dram MCLK=408 Mhz type=1 bus_width=16 size=01000000
[   12.784953] [TTM] Zone  kernel: Available graphics memory: 16380210 kiB
[   12.784954] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   12.784954] [TTM] Initializing pool allocator
[   12.784964] [TTM] Initializing DMA pool allocator
[   13.036775] checking generic (de000000 6c0000) vs hw (de000000 1000000)
[   13.036775] fb: switching to astdrmfb from VESA VGA
[   13.299132] md/raid1:md0: active with 2 out of 2 mirrors
[   13.304440] md0: detected capacity change from 0 to 499970473984
[   13.311544] random: fast init done
[   13.761199] ixgbe: Copyright (c) 1999-2016 Intel Corporation.
[   13.761261] Console: switching to colour dummy device 80x25
[   13.761405] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[   13.761455] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[   13.761458] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[   13.761486] fbcon: astdrmfb (fb0) is primary device
[   14.504339] ixgbe 0000:04:00.0: Multiqueue Enabled: Rx Queue count = 8, Tx Queue count = 8 XDP Queue count = 0
[   14.547375] ixgbe 0000:04:00.0: PCI Express bandwidth of 32GT/s available
[   14.547376] ixgbe 0000:04:00.0: (Speed:8.0GT/s, Width: x4, Encoding Loss:<2%)
[   14.576058] ixgbe 0000:04:00.0: MAC: 4, PHY: 0, PBA No: 020A00-000
[   14.576059] ixgbe 0000:04:00.0: ac:1f:6b:6a:a8:7e
[   14.741565] ixgbe 0000:04:00.0: Intel(R) 10 Gigabit Network Connection
[   15.304828] Console: switching to colour frame buffer device 240x67
[   15.483836] ixgbe 0000:04:00.1: Multiqueue Enabled: Rx Queue count = 8, Tx Queue count = 8 XDP Queue count = 0
[   15.526960] ixgbe 0000:04:00.1: PCI Express bandwidth of 32GT/s available
[   15.526961] ixgbe 0000:04:00.1: (Speed:8.0GT/s, Width: x4, Encoding Loss:<2%)
[   15.555653] ixgbe 0000:04:00.1: MAC: 4, PHY: 0, PBA No: 020A00-000
[   15.555654] ixgbe 0000:04:00.1: ac:1f:6b:6a:a8:7f
[   15.720304] ixgbe 0000:04:00.1: Intel(R) 10 Gigabit Network Connection

```

---

### Post by btodell on 2018-09-13
I also just installed Ubuntu 18.04.1 on a Super Micro server (x10qrh) and the same exact slow boot up graphics are happening to me too.
In addition, the laggy graphics continue even after the system boots to the login prompt.
This lag only happens from the video output from the motherboard. SSH runs at full speed like you'd expect.

I have also recorded video of an LCD monitor connected to the VGA output:
[https://www.youtube.com/watch?v=4VEis5jtsJk](https://www.youtube.com/watch?v=4VEis5jtsJk)
[https://www.youtube.com/watch?v=UonogJOSw3g](https://www.youtube.com/watch?v=UonogJOSw3g)

---

### Post by wildmanne39 on 2018-09-13
Hello and welcome to the forum btodell, please start your own thread instead of posting in someone else's.

Thanks

---

### Post by fomember on 2018-12-15
I have the same issue and opened a bug at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1808183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1808183)
Please have a look at this and eventually tick that you have that problem too.

---

