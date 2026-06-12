---
title: "Not serious, but annoying."
date: 2009-11-23
forum: Hardware
---

### Post by Galban on 2009-11-23
I think nobody does like too see errors messages at any time appearing at the screen.So, I got a question.

Some body here knows if the is any log file where I can see any error message and details at the boot time? I installed start-up manager and I put it to "show text during boot". Now I'm seeing what normally will not see otherwise; an error message about: 

ERROR: pdc: identifying /dev/sda, magic_(bunch of numbers and letters) and couple words/letters more.

In total two messages like this appears; identical. The only difference is the second one is for the sdb driver.

Google-ling I didn't found too much. One thing appears to be a common factor. Those web pages talks about a Bug, but for RAID configurations and I'm not using any raid configuration.

One last detail. With all this thing I have discovered another annoying fact about my computer. My sda Hard Drive is a WD3200AAJS-08B4A0 and my sdb Hard Drive is a WD3200AAJS-00L7A0. The first one is detected at UDMA5 (SATA100) and the second UDMA6 (SATA133). Some where i saw that the firmware is not the same too, but I cant remember the program. I bought it as same model Hard Drives, but performance apparently is different.

Once again. Nothing serious, just annoying! Any ideas will be greatly appreciated.:-k

---

### Post by konradpiskorz on 2009-11-24
I wouldn't worry about it if your hard drive are functioning.  Error messages are a part of life.  You can boot at a higher level of error reporting and have a field day if you really want.

As far as the RAID goes.  You may not be using it, but your controller might support it.  If its a controller specific bug and you're not running RAID it's an inconsequential problem.

To get hard drive info (incl firmware) in the console enter
```
sudo hdparm -i /dev/sda
```
or sdb or hda or whatever your hard drive is.

You can also run

```
sudo lshw
sudo lspci
```

lshw shows you ALL your hardware info.  Will show harddrive firmware also.  You can find your harddrive controller as well.
lspci should be a more manageable list of hardware.

If you post info on your harddrive/controller from that you might get some more info.

my lspci shows
> 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)

my lshw shows
```
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST9250827AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: [REMOVED]
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c25bf563

```

You could look up your controller and see if any bugs are listed.  Usually they're just something really unimportant like some extraneous piece of information available in the hardware that linux doesn't use causes an error.  But since you seem interested I listed these commands.

---

### Post by Galban on 2009-11-26
Thanks for you time and help. I got it solved. As I said I don't have RAID configuration for any of my hard drives. The problem was the software that is supposed to manage RAID configurations. So, tried un-installing the program named "DMRAID" and no more errors messages. Thanks again.

---

