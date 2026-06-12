---
title: "mdadm help"
date: 2015-05-09
forum: Hardware
---

### Post by iLoveLobster on 2015-05-09
Hello, I'm trying to recreate two raid arrays on my computer so I can take the data off. They were created using two different chipset drivers from an old build (Intel and JMicron or Intel I am not sure).

I'm a newb trying to get it to see the drives but running into a few errors. I'm running Ubuntu off a sole SSD. Disabled RAID/Enabled AHCI.

Setup as follows:

SDA - Boot Drive
SDB/SDC = RAID DRIVE 1 - System[SSD]
SDD/SDE = RAID DRIVE 2 - Storage[HDD]

Tried:

```

$sudo mdadm --detail /dev/md0 
mdadm: cannot open /dev/md0: No such file or directory

```

Guess mdadm didnt autoconfig. So tried:

```

[FONT=arial]sudo mdadm --examine /dev/sdb[/FONT]
[FONT=arial]/dev/sdb:[/FONT]
[FONT=arial]          Magic : Intel Raid ISM Cfg Sig.[/FONT]
[FONT=arial]        Version : 1.0.00[/FONT]
[FONT=arial]    Orig Family : bc0328d6[/FONT]
[FONT=arial]         Family : bc0328d6[/FONT]
[FONT=arial]     Generation : 00000625[/FONT]
[FONT=arial]     Attributes : All supported[/FONT]
[FONT=arial]           UUID : 152b8cfb:cff0d96e:a97b5ccf:[/FONT][FONT=arial]66027981[/FONT]
[FONT=arial]       Checksum : d20e316f correct[/FONT]
[FONT=arial]    MPB Sectors : 1[/FONT]
[FONT=arial]          Disks : 2[/FONT]
[FONT=arial]   RAID Devices : 1[/FONT]

[FONT=arial]  Disk01 Serial : 0000114808FF762C[/FONT]
[FONT=arial]          State : active[/FONT]
[FONT=arial]             Id : 00000004[/FONT]
[FONT=arial]    Usable Size : 250065160 (119.24 GiB 128.03 GB)[/FONT]

[FONT=arial][System[SSD]]:[/FONT]
[FONT=arial]           UUID : f3eedf2a:77503aa1:23366ef7:[/FONT][FONT=arial]f9f4b078[/FONT]
[FONT=arial]     RAID Level : 0[/FONT]
[FONT=arial]        Members : 2[/FONT]
[FONT=arial]          Slots : [UU][/FONT]
[FONT=arial]    Failed disk : none[/FONT]
[FONT=arial]      This Slot : 1[/FONT]
[FONT=arial]     Array Size : 500129792 (238.48 GiB 256.07 GB)[/FONT]
[FONT=arial]   Per Dev Size : 250065160 (119.24 GiB 128.03 GB)[/FONT]
[FONT=arial]  Sector Offset : 0[/FONT]
[FONT=arial]    Num Stripes : 976816[/FONT]
[FONT=arial]     Chunk Size : 128 KiB[/FONT]
[FONT=arial]       Reserved : 0[/FONT]
[FONT=arial]  Migrate State : idle[/FONT]
[FONT=arial]      Map State : normal[/FONT]
[FONT=arial]    Dirty State : clean

[/FONT][FONT=arial]  Disk00 Serial : 0000114808FF7661[/FONT]
[FONT=arial]          State : active[/FONT]
[FONT=arial]             Id : 00000005
[/FONT][FONT=arial] Usable Size : 250065160 (119.24 GiB 128.03 GB)[/FONT]

```

For Raid #2
```

[FONT=arial]:[/FONT][FONT=arial]~$ sudo mdadm --examine /dev/sdd[/FONT]
[FONT=arial]mdadm: /dev/sdd is not attached to Intel(R) RAID controller.[/FONT]
[FONT=arial]mdadm: /dev/sdd is not attached to Intel(R) RAID controller.[/FONT]
[FONT=arial]/dev/sdd:[/FONT]
[FONT=arial]          Magic : Intel Raid ISM Cfg Sig.[/FONT]
[FONT=arial]        Version : 1.0.00[/FONT]
[FONT=arial]    Orig Family : a92bba82[/FONT]
[FONT=arial]         Family : a92bba82[/FONT]
[FONT=arial]     Generation : 000001c8[/FONT]
[FONT=arial]     Attributes : All supported[/FONT]
[FONT=arial]           UUID : b8f25ddb:53b3b346:2b42ad33:[/FONT][FONT=arial]90fe5497[/FONT]
[FONT=arial]       Checksum : b223ed18 correct[/FONT]
[FONT=arial]    MPB Sectors : 1[/FONT]
[FONT=arial]          Disks : 2[/FONT]
[FONT=arial]   RAID Devices : 1[/FONT]

[FONT=arial]  Disk00 Serial : MSK5235H2N9LMG[/FONT]
[FONT=arial]          State : active[/FONT]
[FONT=arial]             Id : 00000005[/FONT]
[FONT=arial]    Usable Size : 1953519880 (931.51 GiB 1000.20 GB)[/FONT]

[FONT=arial][Storage[HDD]]:[/FONT]
[FONT=arial]           UUID : 5ae274a7:2b889beb:b53fc0eb:[/FONT][FONT=arial]141e4dec[/FONT]
[FONT=arial]     RAID Level : 0[/FONT]
[FONT=arial]        Members : 2[/FONT]
[FONT=arial]          Slots : [UU][/FONT]
[FONT=arial]    Failed disk : none[/FONT]
[FONT=arial]      This Slot : 0[/FONT]
[FONT=arial]     Array Size : 3907039232 (1863.02 GiB 2000.40 GB)[/FONT]
[FONT=arial]   Per Dev Size : 1953519880 (931.51 GiB 1000.20 GB)[/FONT]
[FONT=arial]  Sector Offset : 0[/FONT]
[FONT=arial]    Num Stripes : 7630936[/FONT]
[FONT=arial]     Chunk Size : 128 KiB[/FONT]
[FONT=arial]       Reserved : 0[/FONT]
[FONT=arial]  Migrate State : idle[/FONT]
[FONT=arial]      Map State : normal[/FONT]
[FONT=arial]    Dirty State : clean[/FONT]

[FONT=arial]  Disk01 Serial : MSK5235H2ND19G[/FONT]
[FONT=arial]          State : active[/FONT]
[FONT=arial]             Id : 00000004[/FONT]
[FONT=arial]    Usable Size : 1953519880 (931.51 GiB 1000.20 GB)[/FONT]
```

Assembling with: 


```
mdadm --assemble --scan
mdadm: Devices UUID-5XXXX and UID-5XXXX have the same name: dev/md/Storage[HDD]
mdadm: Duplicate MD device names in conf file were found.

```

Any ideas?

---

### Post by iLoveLobster on 2015-05-10
^ Anyone halp?

---

### Post by dino99 on 2015-05-10
the latest wiki from the community  [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by iLoveLobster on 2015-05-10
Hey thanks for the reply!

I'm a bit of a noob at Ubuntu/Linux (something I want to use from now on).

If I just need to rebuild the degraded disks from another system, do I need to get the desktop version on the 'alternate' install of Ubuntu?

Is there anyway you can help me with this process?

---

