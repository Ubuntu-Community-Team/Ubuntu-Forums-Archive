---
title: "Assistance with mdadm.conf syntax for reassembly of existing RAID0"
date: 2016-05-27
forum: Hardware
---

### Post by draxbear on 2016-05-27
Hello everyone. I'm trying to recover a friends data from a Sony Vaio VGN-AW47GH Laptop. It has a pair of Toshiba MK5055GS 2.5" 500GB HDD combined (according to my reading) into a 1TB RAID0. The laptop is no longer working so I'm trying to bring them up on my Ubuntu 14.04 system.

I need help with the syntax for the /etc/mdadm/mdadm.conf file to make the RAID0 mountable by Ubuntu. Hopefully someone familiar with mdadm.conf is able to point me in the right direction as the man page and searches online aren't making it clear enough for me to tweak.

They are appearing as /dev/sda & /dev/sdb and I get the following from mdadm examine/scan after running "mdadm --assemble --scan"

```
# mdadm --examine --scan /dev/sda
mdadm: ARRAY line /dev/md/imsm0 has no identity information.
ARRAY metadata=imsm UUID=99fcd315:2ac78f08:08014b0a:33f4585f
ARRAY /dev/md/Volume0 container=99fcd315:2ac78f08:08014b0a:33f4585f member=0 UUID=245d2401:2ad11a3c:6edacb92:47ce3340
```

```
# mdadm --examine --scan /dev/sdb
mdadm: ARRAY line /dev/md/imsm0 has no identity information.
ARRAY metadata=imsm UUID=99fcd315:2ac78f08:08014b0a:33f4585f
ARRAY /dev/md/Volume0 container=99fcd315:2ac78f08:08014b0a:33f4585f member=0 UUID=245d2401:2ad11a3c:6edacb92:47ce3340
```

Here's the exammine results without the --scan option:
```
# mdadm --examine /dev/sda
mdadm: ARRAY line /dev/md/imsm0 has no identity information.
/dev/sda: 
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.0.00
    Orig Family : 08b9238d
         Family : 08b9238d
     Generation : 00001c59
     Attributes : All supported
           UUID : 99fcd315:2ac78f08:08014b0a:33f4585f
       Checksum : 1b2c84f0 correct
    MPB Sectors : 1
          Disks : 2
   RAID Devices : 1

  Disk01 Serial : 9934C0KIT
          State : active
             Id : 00040000
    Usable Size : 976768264 (465.76 GiB 500.11 GB)

[Volume0]: 
           UUID : 245d2401:2ad11a3c:6edacb92:47ce3340
     RAID Level : 0
        Members : 2
          Slots : [_U]
    Failed disk : 0
      This Slot : 1
     Array Size : 1953536000 (931.52 GiB 1000.21 GB)
   Per Dev Size : 976768264 (465.76 GiB 500.11 GB)
  Sector Offset : 0
    Num Stripes : 3815500
     Chunk Size : 128 KiB
       Reserved : 0
  Migrate State : idle
      Map State : normal
    Dirty State : clean

  Disk00 Serial : 9934C0KJT
          State : active failed
             Id : 00000000
    Usable Size : 976768264 (465.76 GiB 500.11 GB)
```

```
# mdadm --examine /dev/sdb
mdadm: ARRAY line /dev/md/imsm0 has no identity information.
/dev/sdb:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.0.00
    Orig Family : 08b9238d
         Family : 08b9238d
     Generation : 00001c59
     Attributes : All supported
           UUID : 99fcd315:2ac78f08:08014b0a:33f4585f
       Checksum : 1b2c84f0 correct
    MPB Sectors : 1
          Disks : 2
   RAID Devices : 1

[Volume0]:
           UUID : 245d2401:2ad11a3c:6edacb92:47ce3340
     RAID Level : 0
        Members : 2
          Slots : [_U]
    Failed disk : 0
      This Slot : ?
     Array Size : 1953536000 (931.52 GiB 1000.21 GB)
   Per Dev Size : 976768264 (465.76 GiB 500.11 GB)
  Sector Offset : 0
    Num Stripes : 3815500
     Chunk Size : 128 KiB
       Reserved : 0
  Migrate State : idle
      Map State : normal
    Dirty State : clean

  Disk00 Serial : 9934C0KJT
          State : active failed
             Id : 00000000
    Usable Size : 976766862 (465.76 GiB 500.10 GB)

  Disk01 Serial : 9934C0KIT
          State : active
             Id : 00040000
    Usable Size : 976766862 (465.76 GiB 500.10 GB)
```

There doesn't appear to be a /dev/md/Volume0 file in dev. There are a few md files now though:
```
# ls -la /dev/md* | grep md
brw-rw---- 1 root disk 9, 126 May 24 22:05 /dev/md126
brw-rw---- 1 root disk 9, 127 May 25 22:27 /dev/md127
/dev/md:
lrwxrwxrwx  1 root root    8 May 25 22:27 imsm0 -> ../md127
```

```
# mdadm --examine --scan /dev/md126
mdadm: ARRAY line /dev/md/imsm0 has no identity information.

```
```
# mdadm --examine --scan /dev/md127
mdadm: ARRAY line /dev/md/imsm0 has no identity information.
ARRAY metadata=imsm UUID=99fcd315:2ac78f08:08014b0a:33f4585f
ARRAY /dev/md/Volume0 container=99fcd315:2ac78f08:08014b0a:33f4585f member=0 UUID=245d2401:2ad11a3c:6edacb92:47ce3340
```

Any and all (constructive) input greatly appreciated!

---

