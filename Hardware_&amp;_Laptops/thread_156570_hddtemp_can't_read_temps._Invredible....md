---
title: "hddtemp can't read temps. Invredible..."
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by flapane on 2006-04-07
/dev/sda: ATA HDS728080PLA380: S.M.A.R.T. not available
flapane@a64:~$ hddtemp /dev/sdb
/dev/sdb: ATA HDT722525DLA380: S.M.A.R.T. not available
flapane@a64:~$ hddtemp /dev/sda1


these are 2hitachi sata2 hd and, as hdparm says and I know, smart is enabled:
 Enabled Supported:
           *    READ BUFFER cmd
           *    WRITE BUFFER cmd
           *    Host Protected Area feature set
           *    Look-ahead
           *    Write cache
           *    Power Management feature set
                Security Mode feature set
           *    SMART feature set
           *    FLUSH CACHE EXT command
           *    Mandatory FLUSH CACHE command
           *    Device Configuration Overlay feature set
           *    48-bit Address feature set
                Automatic Acoustic Management feature set
                SET MAX security extension
                Address Offset Reserved Area Boot
                SET FEATURES subcommand required to spinup after power up
                Power-Up In Standby feature set
                Advanced Power Management feature set
           *    DOWNLOAD MICROCODE cmd
           *    General Purpose Logging feature set
           *    SMART self-test
           *    SMART error logging


what could it be?

---

### Post by flapane on 2006-04-09
up

---

