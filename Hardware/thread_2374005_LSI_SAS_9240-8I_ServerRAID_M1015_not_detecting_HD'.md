---
title: "LSI SAS 9240-8I ServerRAID M1015 not detecting HD's in JBOD mode"
date: 2017-10-11
forum: Hardware
---

### Post by brendanpants on 2017-10-11
[FONT=fixedsys]Greetings! This project has become my white whale. 

New Ubuntu 16.04 server install running off a USB drive (installed, not live). No matter what I do, I can't get Ubuntu to recognize the 3x 4GB WD Red drives. I know they are working because I grabbed a spare SSD and loaded Windows 10 and it was able to detect all three drives. I even formatted one and copied some data just for kicks.

ServeRAID M1015
Firmware 2.120.144-1325

All disks are configured as JBOD, not unconfigured good. I installed megacli and it doesn't recognize the controller...
```

$ sudo megacli -adpCount

Controller Count: 0.


Exit Code: 0x00

$ sudo megacli -v

      MegaCLI SAS RAID Management Tool  Ver 8.07.14 Dec 16, 2013


    (c)Copyright 2013, LSI Corporation, All Rights Reserved.

```

It does recognize the RAID card...

```

$ lspci -vv
...
01:00.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 2008 [Falcon] (rev 02)
        Subsystem: IBM ServeRAID M1015 SAS/SATA Controller
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at e000 [size=256]
        Region 1: Memory at f7c60000 (64-bit, non-prefetchable) [size=16K]
        Region 3: Memory at f7c00000 (64-bit, non-prefetchable) [size=256K]
        Expansion ROM at f7c40000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel modules: megaraid_sas

```

And I tried installing the newest drivers from broadcom...

```

$ sudo dpkg -i megaraid_sas_07.703.05.00-1-ubuntu16.04_x86_64.deb
Selecting previously unselected package megaraid-sas.
(Reading database ... 178410 files and directories currently installed.)
Preparing to unpack megaraid_sas_07.703.05.00-1-ubuntu16.04_x86_64.deb ...
pre 07.703.05.00
Unpacking megaraid-sas (07.703.05.00-1) ...
Setting up megaraid-sas (07.703.05.00-1) ...
post 07.703.05.00
post Install Done.

```


I feel like i must be doing something stupid, but I can't figure it out...

```

$ lsblk
NAME                 MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                    8:0    1 29.9G  0 disk
ââsda1                 8:1    1  487M  0 part  /boot
ââsda2                 8:2    1    1K  0 part
ââsda5                 8:5    1 29.4G  0 part
  ââleela--vg-swap_1 252:0    0 15.7G  0 lvm
  â ââcryptswap1     252:2    0 15.7G  0 crypt [SWAP]
  ââleela--vg-root   252:1    0 13.6G  0 lvm   /
$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/leela-vg/root
  LV Name                root
  VG Name                leela-vg
  LV UUID                HyqwQW-PvuE-z9cy-MAo5-37l3-DTGz-Iis3lj
  LV Write Access        read/write
  LV Creation host, time leela, 2017-10-11 09:49:27 -0600
  LV Status              available
  # open                 1
  LV Size                13.63 GiB
  Current LE             3490
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1


  --- Logical volume ---
  LV Path                /dev/leela-vg/swap_1
  LV Name                swap_1
  VG Name                leela-vg
  LV UUID                bTZoKG-3KEd-KLFm-DpdB-2LEE-DbMa-QTUrDe
  LV Write Access        read/write
  LV Creation host, time leela, 2017-10-11 09:49:27 -0600
  LV Status              available
  # open                 1
  LV Size                15.70 GiB
  Current LE             4019
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
[/FONT]$ ls /dev
autofs           fuse       loop2                    ptmx      tty11  tty30  tty5       ttyS1   ttyS29   vcs7
block            hidraw0    loop3                    pts       tty12  tty31  tty50      ttyS10  ttyS3    vcsa
bsg              hpet       loop4                    random    tty13  tty32  tty51      ttyS11  ttyS30   vcsa1
btrfs-control    hugepages  loop5                    rfkill    tty14  tty33  tty52      ttyS12  ttyS31   vcsa2
bus              hwrng      loop6                    rtc       tty15  tty34  tty53      ttyS13  ttyS4    vcsa3
char             i2c-0      loop7                    rtc0      tty16  tty35  tty54      ttyS14  ttyS5    vcsa4
console          i2c-1      loop-control             sda       tty17  tty36  tty55      ttyS15  ttyS6    vcsa5
core             i2c-2      mapper                   sda1      tty18  tty37  tty56      ttyS16  ttyS7    vcsa6
cpu              i2c-3      mcelog                   sda2      tty19  tty38  tty57      ttyS17  ttyS8    vcsa7
cpu_dma_latency  i2c-4      megaraid_sas_ioctl_node  sda5      tty2   tty39  tty58      ttyS18  ttyS9    vfio
cuse             i2c-5      mei0                     sg0       tty20  tty4   tty59      ttyS19  uhid     vga_arbiter
disk             i2c-6      mem                      shm       tty21  tty40  tty6       ttyS2   uinput   vhci
dm-0             initctl    memory_bandwidth         snapshot  tty22  tty41  tty60      ttyS20  urandom  vhost-net
dm-1             input      mqueue                   snd       tty23  tty42  tty61      ttyS21  userio   zero
dm-2             kmsg       net                      stderr    tty24  tty43  tty62      ttyS22  vcs
dri              kvm        network_latency          stdin     tty25  tty44  tty63      ttyS23  vcs1
drm_dp_aux0      leela-vg   network_throughput       stdout    tty26  tty45  tty7       ttyS24  vcs2
ecryptfs         lightnvm   null                     tty       tty27  tty46  tty8       ttyS25  vcs3
fb0              log        port                     tty0      tty28  tty47  tty9       ttyS26  vcs4
fd               loop0      ppp                      tty1      tty29  tty48  ttyprintk  ttyS27  vcs5
full             loop1      psaux                    tty10     tty3   tty49  ttyS0      ttyS28  vcs6
[FONT=fixedsys]
```[/FONT]
[FONT=fixedsys]
Any ideas or thoughts?

Thanks![/FONT]

---

### Post by SCUZNUTS on 2018-02-26
Did you ever get anywhere with this?
I am now in the exact same situation.

---

### Post by wildmanne39 on 2018-02-26
Hello SCUZNUTS, please start your own thread the OP of this old thread has not been back since he created the thread.

Thanks

---

