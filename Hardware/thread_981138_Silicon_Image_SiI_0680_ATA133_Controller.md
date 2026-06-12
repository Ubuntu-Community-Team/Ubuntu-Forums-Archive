---
title: "Silicon Image SiI 0680 ATA/133 Controller"
date: 2008-11-13
forum: Hardware
---

### Post by Atsuko on 2008-11-13
How would I get the Silicon Image SiI 0680 ATA/133 Controller working ?
I have drivers for windows but haven't found anything for ubuntu.
Windows driver is UATA133PCI_Win95-XP_v1.0729a

It's made by [SIIG](http://siig.com/) 
But they don't even list it now on their web site.

---

### Post by KuBala on 2008-12-17
I have the same controller card in my desktop. I used it's bios to create a raid0 set. XP sees it as one drive array like it should, and can be partitioned in the installer. Unfortunately ubuntu 8.10 sees 2 hard drives. I think it does not support the card. Did you find any workaround?

---

### Post by Aacron on 2009-06-22
I also have this problem.  Windows XP SP3 even does funky things with this as well (installs mbr to wrong drive 99% of the time).

I'd really like to get some help with this as it is really messing me up.  I installed Windows, then Linux (like ya should), and grub gave me error 17, which I google'd to mean it can't find the partitions.

Windows XP detects the drives correctly (mostly):
80GB (Windows) on mobo IDE (1,0)
2x40GB (Games/Backups) RAID1 Pri Master/Sec Master on the 680 (0,1)
40GB (Ubuntu) on 680 Pr Slave (this ends up being 0,0)

I end up with Ubuntu seeing this:
sda: Windows Drive
sdb: first drive on RAID (unrecognised)
sdc: Ubuntu
sdd: second drive on RAID (unrecognised)

Just to get it where I can even get *into* Ubuntu, I had to use some convoluted hack to get grub4dos to load grub through ntldr, so I go through two (!!) boot-loaders to get to Ubuntu.  I'm not a very happy panda :(

If anyone knows a way to: a) get Ubuntu to properly recognise the sil0680 drives, and b) help me to get GRUB properly installed, I'd *really* appreciate it!

Edit:
For a little more information here is my set-up:
AMD Sempron 3200+
K9N Neo-F v1.0 (nVidia 550 MCP)
ATI Radeon x1650
Audigy 2 zx
Sil0680 PCI-PATA controller

Onboard IDE:
80GB Windows XP Pro, Plextor DVD-RW

Sil0680:
40GB WD400 Raid1,1 (Backup/Games), Maxtor 40GB Ubuntu (channel 0)
40GB WD400 Raid1,2 (Backup/Games) (Channel 1)

---

### Post by Aacron on 2009-06-23
use dmraid.

I'm about to give it a whirl myself... wish me luck :P

I solved my GRUB problems, though... perhaps some of the info will help anyone who filds this out:
[http://ubuntuforums.org/showthread.php?p=7502220#post7502220](http://ubuntuforums.org/showthread.php?p=7502220#post7502220)

---

### Post by Aacron on 2009-06-23
dmraid doesnt' seem to work... 

I've been lookign around and it does seem that the linux kernel could support it, but when I looked in the config for the kernel there are a few lines that I've noticed are missing, and I'm wonderign if I can just add them and it work, or if I can ruin my kernel or something by doing this:

from [http://www.linuxquestions.org/questions/linux-hardware-18/file-systems-corrupting-on-sil0680-cards-288379/ ]("http://www.linuxquestions.org/questions/linux-hardware-18/file-systems-corrupting-on-sil0680-cards-288379/")
> 
Silicon Image Ide controllers should use the CMD640 chipset.
 I'd try configuring the kernel in the IDE section as follows:
 
 CONFIG_BLK_DEV_CMD640=y --------------------------------------------------> this
 # CONFIG_BLK_DEV_CMD640_ENHANCED is not set
 # CONFIG_BLK_DEV_ISAPNP is not set
 CONFIG_BLK_DEV_IDEPCI=y
 CONFIG_BLK_DEV_GENERIC=y
 CONFIG_IDEPCI_SHARE_IRQ=y
 CONFIG_BLK_DEV_IDEDMA_PCI=y
 # CONFIG_BLK_DEV_OFFBOARD is not set
 # CONFIG_BLK_DEV_IDEDMA_FORCED is not set
 CONFIG_IDEDMA_PCI_AUTO=y
 # CONFIG_IDEDMA_ONLYDISK is not set
 CONFIG_BLK_DEV_IDEDMA=y
 # CONFIG_IDEDMA_PCI_WIP is not set
 CONFIG_BLK_DEV_ADMA100=y
 CONFIG_BLK_DEV_AEC62XX=y
 CONFIG_BLK_DEV_ALI15X3=y
 # CONFIG_WDC_ALI15X3 is not set
 CONFIG_BLK_DEV_AMD74XX=y
 # CONFIG_AMD74XX_OVERRIDE is not set
 CONFIG_BLK_DEV_ATIIXP=y
 CONFIG_BLK_DEV_CMD64X=y -------------------------------------------------this
 CONFIG_BLK_DEV_TRIFLEX=y
 # CONFIG_BLK_DEV_CY82C693 is not set
 CONFIG_BLK_DEV_CS5530=y
 CONFIG_BLK_DEV_HPT34X=y
 # CONFIG_HPT34X_AUTODMA is not set
 CONFIG_BLK_DEV_HPT366=y
 CONFIG_BLK_DEV_PIIX=y
 # CONFIG_BLK_DEV_NS87415 is not set
 # CONFIG_BLK_DEV_OPTI621 is not set
 CONFIG_BLK_DEV_PDC202XX_OLD=y
 # CONFIG_PDC202XX_BURST is not set
 CONFIG_BLK_DEV_PDC202XX_NEW=y
 # CONFIG_PDC202XX_FORCE is not set
 CONFIG_BLK_DEV_RZ1000=y
 CONFIG_BLK_DEV_SC1200=y
 CONFIG_BLK_DEV_SVWKS=y
 CONFIG_BLK_DEV_SIIMAGE=y ---------------------------------------------- This shouldn't be necessary (I have on the same box a 2.6 kernel working fine with this module commented
 CONFIG_BLK_DEV_SIS5513=y
 CONFIG_BLK_DEV_SLC90E66=y
 # CONFIG_BLK_DEV_TRM290 is not set
 CONFIG_BLK_DEV_VIA82CXXX=y
 CONFIG_IDE_CHIPSETS=y
 This .config file comes from the Slackware 2.4.26 standard kernel. 
 I have the same PCI IDE controller on an asus P4PE mobo working fine with this configuration. You can comment out the lines you do not need of course. I'd check the IDE cables as well trying a good quality one (with triple wiring), if you already do not have one.
 Hope this helps
 Ciao.


And this is my /boot/config-2.6.28-13-generic :
```

CONFIG_BLK_CPQ_CISS_DA=m
CONFIG_BLK_CPQ_DA=m
CONFIG_BLK_DEV=y
CONFIG_BLK_DEV_3W_XXXX_RAID=m
# CONFIG_BLK_DEV_BSG is not set
CONFIG_BLK_DEV_COMPCACHE=m
# CONFIG_BLK_DEV_COMPCACHE_DEBUG is not set
# CONFIG_BLK_DEV_COMPCACHE_STATS is not set
# CONFIG_BLK_DEV_COW_COMMON is not set
CONFIG_BLK_DEV_CRYPTOLOOP=m
CONFIG_BLK_DEV_DAC960=m
CONFIG_BLK_DEV_DM=y
CONFIG_BLK_DEV_DM_BBR=m
CONFIG_BLK_DEV_DRBD=m
CONFIG_BLK_DEV_FD=m
# CONFIG_BLK_DEV_HD is not set
CONFIG_BLK_DEV_INITRD=y
CONFIG_BLK_DEV_INTEGRITY=y
CONFIG_BLK_DEV_IO_TRACE=y
CONFIG_BLK_DEV_LOOP=y
CONFIG_BLK_DEV_MD=y
CONFIG_BLK_DEV_NBD=m
CONFIG_BLK_DEV_RAM=y
CONFIG_BLK_DEV_RAM_COUNT=16
CONFIG_BLK_DEV_RAM_SIZE=65536
CONFIG_BLK_DEV_SD=y
CONFIG_BLK_DEV_SR=y
# CONFIG_BLK_DEV_SR_VENDOR is not set
CONFIG_BLK_DEV_SX8=m
# CONFIG_BLK_DEV_UB is not set
CONFIG_BLK_DEV_UMEM=m
# CONFIG_BLK_DEV_XD is not set
# CONFIG_BLK_DEV_XIP is not set
CONFIG_BLOCK=y
CONFIG_BNX2=m

```

So does Ubuntu not have the driver installed, or can I just add the lines in the post from other forum and it work?  Do i need to recompile kernel?  What's up?

---

### Post by Aacron on 2009-06-23
Something else I noticed today when I did the ubuntu "system test":
> 
Volume (silicon_medley_raid_member)
Property    Value
info.category    volume
info.product    Volume (silicon_medley_raid_member)
info.udi    /org/freedesktop/Hal/devices/volume_part1_size_39999967744
info.parent    /org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD400BB_75FWD_WCAJC2544398
info.capabilities    volume block
volume.is_mounted_read_only    False
volume.mount_point    
volume.uuid    
volume.is_mounted    False
volume.is_partition    True
volume.partition.start    32256
volume.partition.media_size    40000000000
volume.partition.number    1
volume.label    
volume.fstype    silicon_medley_raid_member
volume.fsusage    raid
volume.is_disc    False
volume.fsversion    0.0
volume.linux.is_device_mapper    False
volume.block_size    512
volume.num_blocks    78124937
volume.size    39999967744
block.device    /dev/sdb1
block.major    8
block.is_volume    True
block.storage_device    /org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD400BB_75FWD_WCAJC2544398
block.minor    17
linux.hotplug_type    3
linux.sysfs_path    /sys/devices/pci0000:00/0000:00:06.0/0000:01:02.0/host6/target6:0:0/6:0:0:0/block/sdb/sdb1 

So I'm now more confused than I was before... how do I *access* my raid set?

---

