---
title: "ACPI Warning: SystemIO  conflicts with Op"
date: 2016-10-16
forum: Hardware
---

### Post by valereguerin on 2016-10-16
hi,

Kernel logs: 

ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x000000000000042C-0x000000000000042D (\GP2C) (20160422/utaddress-255)

EXT4-fs (sdb6): warning: mounting unchecked fs, running e2fsck is recommended
EXT4-fs (sdb6): error count since last fsck: 52

EXT4-fs (sdb6): initial error at time 1448104240: ext4_mb_generate_buddy:756
EXT4-fs (sdb6): last error at time 1476406729: ext4_mb_generate_buddy:756



Thanks for regards,


ubuntu 14.04  kernel 4.8.1 040801 Gigabit G1 Sniper x86_64 WD caviar Green 2to

Thank you to anyone who might be able to help.

---

### Post by valereguerin on 2016-10-27
on my Desktop & on my Laptop now,..... good !    :guitar:

```
4.868995] Btrfs loaded
[    4.998445] BTRFS: device fsid d46933e7-3751-4b40-95a9-d05fe377fbdd devid 1 transid 6647 /dev/sda6
[    5.013766] BTRFS info (device sda6): disk space caching is enabled
[    5.202630] random: init: uninitialized urandom read (12 bytes read, 77 bits of entropy available)
[    7.463083] random: nonblocking pool is initialized
[    8.008940] Adding 1047548k swap on /dev/sda5.  Priority:-1 extents:1 across:1047548k FS
[    8.031690] BTRFS info (device sda6): disk space caching is enabled
[    8.159419] EXT4-fs (sda7): mounting ext2 file system using the ext4 subsystem
[    8.166120] EXT4-fs (sda7): mounted filesystem without journal. Opts: (null)
[    8.172399] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[    8.175966] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[    8.325494] systemd-udevd[501]: starting version 204
[    8.416088] lp: driver loaded but no devices found
[    8.449560] ppdev: user-space parallel port driver
[    8.641120] wmi: Mapper loaded
[    8.695485] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.23
[    8.712155] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[COLOR=#ff0000][    8.739958] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) [/COLOR](20150930/utaddress-254)
[    8.739968] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.739989] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[    8.739994] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.739996] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[    8.740000] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.740018] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[    8.740023] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.740024] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.770805] input: Toshiba input device as /devices/virtual/input/input8
```

Ubuntu Unity 7.2.6  Kernel   4.4.0.45 generic x86-64  Fresh install

Laptop : L505 13 j Toshiba Satellite


since 2011....
                                                                                                                                                             December 21st, 2011                                                                                                                                                                                                     [#5]("https://ubuntuforums.org/showthread.php?t=1810223&p=11553437#post11553437")                                                                                                                                                                                              
                                                             [                                                      [IMG]https://ubuntuforums.org/customavatars/avatar12502_6.gif[/IMG]                                              ]("https://ubuntuforums.org/member.php?u=12502")                                                                                     [**[COLOR=#000000]TechZilla[/COLOR]**]("https://ubuntuforums.org/member.php?u=12502")      
                         [IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]                                                                    Just Give Me the Beans!                                                                   [IMG]https://ubuntuforums.org/images/rank_3.png[/IMG]                                                                                                                                                                [IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/im_aim.gif[/IMG]  [IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/im_yahoo.gif[/IMG] [IMG]http://mystatus.skype.com/smallicon/cyberpunkspike[/IMG]                         
                                      
             
                                                   Join DateMar 2005LocationOhio, USABeans61DistroUbuntu 12.04 Precise Pangolin                                                           
                      
     
                                          **Re: ACPI Warning: Incorrect checksum in table [TAMG] - 0xD6, should be 0xD5**[INDENT]                     It is actually fairly common, to have some sort of ACPI warning these days!


Its not great, but it should not pose any noticeable problem. If the bug  is not in feature critical table, or can be read regardless, it should  not have affect.  Many systems I watched boot, have some ACPI warning  displayed.  Now when I'm at the data center, or on my workstation  (SuperMicro Mobo), The warnings are suspiciously absent. I think the  manufacturers put more time into the Server class Motherboard Bios.

Really, it is a bug in your ACPI section  of the BIOS.  If it can be fixed with a BIOS update, then I would  update.  If The bug is not fixed in an update, I would email the  manufacture, as they might not even know.  Remember only a small section  use Linux, even less own your board, and even less still would report  the error.                 

No support driver no support software.......GOOD  very good...
LTS you say....
9 years for Patch Kernel security   ...maybe ACPI Problem will be Good in 2050....I Hope !
[/INDENT]

---

