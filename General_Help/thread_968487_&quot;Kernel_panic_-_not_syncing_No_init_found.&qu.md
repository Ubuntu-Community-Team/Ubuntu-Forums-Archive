---
title: "&quot;Kernel panic - not syncing: No init found.&quot;"
date: 2008-11-02
forum: General Help
---

### Post by computer_freak_8 on 2008-11-02
I hope I put this thread in the right spot; sorry if it's not.

Okay, so I found this tutorial for compiling a kernel. Since I heard about it, I've always thought it was something I should try sometime. So I finally did. 

I have seen this error on all sorts of different forums/mailing lists/et cetera on the Internet, but I haven't yet found a solid answer as to how to fix it.

I compiled my kernel by executing:

```
$ make menuconfig
$ make
$ make modules
# make install 
# cd /boot
# mkinitramfs -o initrd.img-2.6.27.4 2.6.27.4
```

The last few lines shown on my screen after I boot are:
> 
Failed to execute /init
Failed to execute /sbin/init. Attempting defaults...
Kernel panic - not syncing: No init found. Try passing init= option to kernel.

Each of the lines has a number in front of it, in kind of a [79.293748190] format.
During the kernel panic, I notice that my Caps Lock and Scroll Lock lights on my keyboard are flashing in sync with each other. Also, I have to do a hard reset - [Ctrl]+[Alt]+[Delete] does nothing.

When I first tried it, my /boot/grub/menu.lst file did not have an "init=" option. So I added it. Same error.
Here is a snippet of my current /boot/grub/menu.lst file:```

title		Ubuntu 8.04.1, kernel vmlinuz-2.6.27.4
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27.4 init=/sbin/init root=/dev/sda7 ro
initrd		/boot/initrd.img-2.6.27.4

title		Ubuntu 8.04.1, kernel vmlinuz-2.6.27.4 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27.4 init=/sbin/init root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.27.4

### Let's hope that worked...


title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=/dev/sda7
#UUID=ffa3fcb6-4e46-454b-b7fb-b08a372e0fc0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
#quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda7 ro single
#UUID=ffa3fcb6-4e46-454b-b7fb-b08a372e0fc0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

```
The first two entries are the kernel panic ones. The other four boot fine.

I've seen references to missing filesystem/hard drive device support compiled into the kernel. So, here are some parts from my .config file that I generated before compiling the kernel:```
#
# Executable file formats / Emulations
#
CONFIG_BINFMT_ELF=y
CONFIG_COMPAT_BINFMT_ELF=y
CONFIG_BINFMT_MISC=y
CONFIG_IA32_EMULATION=y
CONFIG_IA32_AOUT=m
CONFIG_COMPAT=y
CONFIG_COMPAT_FOR_U64_ALIGNMENT=y
CONFIG_SYSVIPC_COMPAT=y
CONFIG_NET=y

#
# SCSI device support
#
CONFIG_RAID_ATTRS=m
CONFIG_SCSI=y
CONFIG_SCSI_DMA=y
CONFIG_SCSI_TGT=y
CONFIG_SCSI_NETLINK=y
CONFIG_SCSI_PROC_FS=y

#
# SCSI support type (disk, tape, CD-ROM)
#
CONFIG_BLK_DEV_SD=y
CONFIG_CHR_DEV_ST=y
CONFIG_CHR_DEV_OSST=y
CONFIG_BLK_DEV_SR=y
CONFIG_BLK_DEV_SR_VENDOR=y
CONFIG_CHR_DEV_SG=y
CONFIG_CHR_DEV_SCH=y

#
# Some SCSI devices (e.g. CD jukebox) support multiple LUNs
#
CONFIG_SCSI_MULTI_LUN=y
CONFIG_SCSI_CONSTANTS=y
CONFIG_SCSI_LOGGING=y
CONFIG_SCSI_SCAN_ASYNC=y
CONFIG_SCSI_WAIT_SCAN=m

#
# SCSI Transports
#
CONFIG_SCSI_SPI_ATTRS=m
CONFIG_SCSI_FC_ATTRS=m
CONFIG_SCSI_FC_TGT_ATTRS=y
CONFIG_SCSI_ISCSI_ATTRS=m
CONFIG_SCSI_SAS_ATTRS=m
CONFIG_SCSI_SAS_LIBSAS=m
CONFIG_SCSI_SAS_ATA=y
CONFIG_SCSI_SAS_HOST_SMP=y
# CONFIG_SCSI_SAS_LIBSAS_DEBUG is not set
CONFIG_SCSI_SRP_ATTRS=m
CONFIG_SCSI_SRP_TGT_ATTRS=y
CONFIG_SCSI_LOWLEVEL=y
CONFIG_ISCSI_TCP=m
CONFIG_BLK_DEV_3W_XXXX_RAID=m
CONFIG_SCSI_3W_9XXX=m
CONFIG_SCSI_ACARD=m
CONFIG_SCSI_AACRAID=m
CONFIG_SCSI_AIC7XXX=m
CONFIG_AIC7XXX_CMDS_PER_DEVICE=8
CONFIG_AIC7XXX_RESET_DELAY_MS=15000
CONFIG_AIC7XXX_DEBUG_ENABLE=y
CONFIG_AIC7XXX_DEBUG_MASK=0
CONFIG_AIC7XXX_REG_PRETTY_PRINT=y
# CONFIG_SCSI_AIC7XXX_OLD is not set
CONFIG_SCSI_AIC79XX=m
CONFIG_AIC79XX_CMDS_PER_DEVICE=32
CONFIG_AIC79XX_RESET_DELAY_MS=15000
CONFIG_AIC79XX_DEBUG_ENABLE=y
CONFIG_AIC79XX_DEBUG_MASK=0
CONFIG_AIC79XX_REG_PRETTY_PRINT=y
CONFIG_SCSI_AIC94XX=m
# CONFIG_AIC94XX_DEBUG is not set
# CONFIG_SCSI_DPT_I2O is not set
CONFIG_SCSI_ADVANSYS=m
CONFIG_SCSI_ARCMSR=m
CONFIG_SCSI_ARCMSR_AER=y
CONFIG_MEGARAID_NEWGEN=y
CONFIG_MEGARAID_MM=m
CONFIG_MEGARAID_MAILBOX=m
CONFIG_MEGARAID_LEGACY=m
CONFIG_MEGARAID_SAS=m
CONFIG_SCSI_HPTIOP=m
CONFIG_SCSI_BUSLOGIC=m
CONFIG_SCSI_DMX3191D=m
CONFIG_SCSI_EATA=m
CONFIG_SCSI_EATA_TAGGED_QUEUE=y
CONFIG_SCSI_EATA_LINKED_COMMANDS=y
CONFIG_SCSI_EATA_MAX_TAGS=16
CONFIG_SCSI_FUTURE_DOMAIN=m
CONFIG_SCSI_GDTH=m
CONFIG_SCSI_IPS=m
CONFIG_SCSI_INITIO=m
CONFIG_SCSI_INIA100=m
CONFIG_SCSI_PPA=m
CONFIG_SCSI_IMM=m
# CONFIG_SCSI_IZIP_EPP16 is not set
# CONFIG_SCSI_IZIP_SLOW_CTR is not set
# CONFIG_SCSI_MVSAS is not set
CONFIG_SCSI_STEX=m
CONFIG_SCSI_SYM53C8XX_2=m
CONFIG_SCSI_SYM53C8XX_DMA_ADDRESSING_MODE=1
CONFIG_SCSI_SYM53C8XX_DEFAULT_TAGS=16
CONFIG_SCSI_SYM53C8XX_MAX_TAGS=64
CONFIG_SCSI_SYM53C8XX_MMIO=y
CONFIG_SCSI_IPR=m
# CONFIG_SCSI_IPR_TRACE is not set
# CONFIG_SCSI_IPR_DUMP is not set
CONFIG_SCSI_QLOGIC_1280=m
CONFIG_SCSI_QLA_FC=m
CONFIG_SCSI_QLA_ISCSI=m
CONFIG_SCSI_LPFC=m
CONFIG_SCSI_DC395x=m
CONFIG_SCSI_DC390T=m
CONFIG_SCSI_DEBUG=m
CONFIG_SCSI_SRP=m
CONFIG_SCSI_LOWLEVEL_PCMCIA=y
CONFIG_PCMCIA_FDOMAIN=m
CONFIG_PCMCIA_QLOGIC=m
CONFIG_PCMCIA_SYM53C500=m
# CONFIG_SCSI_DH is not set
CONFIG_ATA=m
# CONFIG_ATA_NONSTANDARD is not set
CONFIG_ATA_ACPI=y
CONFIG_SATA_PMP=y
CONFIG_SATA_AHCI=m
CONFIG_SATA_SIL24=m
CONFIG_ATA_SFF=y
CONFIG_SATA_SVW=m
CONFIG_ATA_PIIX=m
CONFIG_SATA_MV=m
CONFIG_SATA_NV=m
CONFIG_PDC_ADMA=m
CONFIG_SATA_QSTOR=m
CONFIG_SATA_PROMISE=m
CONFIG_SATA_SX4=m
CONFIG_SATA_SIL=m
CONFIG_SATA_SIS=m
CONFIG_SATA_ULI=m
CONFIG_SATA_VIA=m
CONFIG_SATA_VITESSE=m
CONFIG_SATA_INIC162X=m
CONFIG_PATA_ACPI=m
# CONFIG_PATA_ALI is not set
CONFIG_PATA_AMD=m
CONFIG_PATA_ARTOP=m
CONFIG_PATA_ATIIXP=m
# CONFIG_PATA_CMD640_PCI is not set
CONFIG_PATA_CMD64X=m
CONFIG_PATA_CS5520=m
# CONFIG_PATA_CS5530 is not set
# CONFIG_PATA_CYPRESS is not set
CONFIG_PATA_EFAR=m
CONFIG_ATA_GENERIC=m
CONFIG_PATA_HPT366=m
# CONFIG_PATA_HPT37X is not set
# CONFIG_PATA_HPT3X2N is not set
CONFIG_PATA_HPT3X3=m
# CONFIG_PATA_HPT3X3_DMA is not set
CONFIG_PATA_IT821X=m
CONFIG_PATA_IT8213=m
CONFIG_PATA_JMICRON=m
CONFIG_PATA_TRIFLEX=m
CONFIG_PATA_MARVELL=m
CONFIG_PATA_MPIIX=m
CONFIG_PATA_OLDPIIX=m
CONFIG_PATA_NETCELL=m
# CONFIG_PATA_NINJA32 is not set
# CONFIG_PATA_NS87410 is not set
# CONFIG_PATA_NS87415 is not set
# CONFIG_PATA_OPTI is not set
# CONFIG_PATA_OPTIDMA is not set
CONFIG_PATA_PCMCIA=m
# CONFIG_PATA_PDC_OLD is not set
# CONFIG_PATA_RADISYS is not set
CONFIG_PATA_RZ1000=m
# CONFIG_PATA_SC1200 is not set
CONFIG_PATA_SERVERWORKS=m
CONFIG_PATA_PDC2027X=m
CONFIG_PATA_SIL680=m
CONFIG_PATA_SIS=m
CONFIG_PATA_VIA=m
CONFIG_PATA_WINBOND=m
CONFIG_PATA_PLATFORM=m
# CONFIG_PATA_SCH is not set
CONFIG_MD=y
CONFIG_BLK_DEV_MD=m
CONFIG_MD_LINEAR=m
CONFIG_MD_RAID0=m
CONFIG_MD_RAID1=m
CONFIG_MD_RAID10=m
CONFIG_MD_RAID456=m
CONFIG_MD_RAID5_RESHAPE=y
CONFIG_MD_MULTIPATH=m
CONFIG_MD_FAULTY=m
CONFIG_BLK_DEV_DM=m
# CONFIG_DM_DEBUG is not set
CONFIG_DM_CRYPT=m
CONFIG_DM_SNAPSHOT=m
CONFIG_DM_MIRROR=m
CONFIG_DM_ZERO=m
CONFIG_DM_MULTIPATH=m
# CONFIG_DM_DELAY is not set
CONFIG_DM_UEVENT=y
CONFIG_FUSION=y
CONFIG_FUSION_SPI=m
CONFIG_FUSION_FC=m
CONFIG_FUSION_SAS=m
CONFIG_FUSION_MAX_SGE=128
CONFIG_FUSION_CTL=m
CONFIG_FUSION_LAN=m
CONFIG_FUSION_LOGGING=y

#
# File systems
#
CONFIG_EXT2_FS=y
CONFIG_EXT2_FS_XATTR=y
CONFIG_EXT2_FS_POSIX_ACL=y
CONFIG_EXT2_FS_SECURITY=y
CONFIG_EXT2_FS_XIP=y
CONFIG_FS_XIP=y
CONFIG_EXT3_FS=y
CONFIG_EXT3_FS_XATTR=y
CONFIG_EXT3_FS_POSIX_ACL=y
CONFIG_EXT3_FS_SECURITY=y
CONFIG_EXT4DEV_FS=y
CONFIG_EXT4DEV_FS_XATTR=y
CONFIG_EXT4DEV_FS_POSIX_ACL=y
CONFIG_EXT4DEV_FS_SECURITY=y
CONFIG_JBD=y
CONFIG_JBD_DEBUG=y
CONFIG_JBD2=y
CONFIG_JBD2_DEBUG=y
CONFIG_FS_MBCACHE=y
CONFIG_REISERFS_FS=y
CONFIG_REISERFS_CHECK=y
CONFIG_REISERFS_PROC_INFO=y
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y
CONFIG_JFS_FS=y
CONFIG_JFS_POSIX_ACL=y
CONFIG_JFS_SECURITY=y
CONFIG_JFS_DEBUG=y
CONFIG_JFS_STATISTICS=y
CONFIG_FS_POSIX_ACL=y
CONFIG_XFS_FS=y
CONFIG_XFS_QUOTA=y
CONFIG_XFS_POSIX_ACL=y
CONFIG_XFS_RT=y
# CONFIG_XFS_DEBUG is not set
CONFIG_GFS2_FS=y
CONFIG_GFS2_FS_LOCKING_DLM=m
CONFIG_OCFS2_FS=y
CONFIG_OCFS2_FS_O2CB=y
CONFIG_OCFS2_FS_USERSPACE_CLUSTER=m
CONFIG_OCFS2_FS_STATS=y
CONFIG_OCFS2_DEBUG_MASKLOG=y
CONFIG_OCFS2_DEBUG_FS=y
CONFIG_DNOTIFY=y
CONFIG_INOTIFY=y
CONFIG_INOTIFY_USER=y
CONFIG_QUOTA=y
CONFIG_QUOTA_NETLINK_INTERFACE=y
CONFIG_PRINT_QUOTA_WARNING=y
CONFIG_QFMT_V1=y
CONFIG_QFMT_V2=y
CONFIG_QUOTACTL=y
CONFIG_AUTOFS_FS=y
CONFIG_AUTOFS4_FS=y
CONFIG_FUSE_FS=y
CONFIG_GENERIC_ACL=y

#
# CD-ROM/DVD Filesystems
#
CONFIG_ISO9660_FS=y
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_UDF_FS=y
CONFIG_UDF_NLS=y

#
# DOS/FAT/NT Filesystems
#
CONFIG_FAT_FS=y
CONFIG_MSDOS_FS=y
CONFIG_VFAT_FS=y
CONFIG_FAT_DEFAULT_CODEPAGE=437
CONFIG_FAT_DEFAULT_IOCHARSET="iso8859-1"
CONFIG_NTFS_FS=y
CONFIG_NTFS_DEBUG=y
CONFIG_NTFS_RW=y

#
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_PROC_VMCORE=y
CONFIG_PROC_SYSCTL=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
CONFIG_TMPFS_POSIX_ACL=y
CONFIG_HUGETLBFS=y
CONFIG_HUGETLB_PAGE=y
CONFIG_CONFIGFS_FS=y

#
# Miscellaneous filesystems
#
CONFIG_ADFS_FS=y
CONFIG_ADFS_FS_RW=y
CONFIG_AFFS_FS=y
CONFIG_ECRYPT_FS=y
CONFIG_HFS_FS=y
CONFIG_HFSPLUS_FS=y
CONFIG_BEFS_FS=y
CONFIG_BEFS_DEBUG=y
CONFIG_BFS_FS=y
CONFIG_EFS_FS=y
CONFIG_JFFS2_FS=m
CONFIG_JFFS2_FS_DEBUG=0
CONFIG_JFFS2_FS_WRITEBUFFER=y
CONFIG_JFFS2_FS_WBUF_VERIFY=y
CONFIG_JFFS2_SUMMARY=y
CONFIG_JFFS2_FS_XATTR=y
CONFIG_JFFS2_FS_POSIX_ACL=y
CONFIG_JFFS2_FS_SECURITY=y
CONFIG_JFFS2_COMPRESSION_OPTIONS=y
CONFIG_JFFS2_ZLIB=y
CONFIG_JFFS2_LZO=y
CONFIG_JFFS2_RTIME=y
CONFIG_JFFS2_RUBIN=y
# CONFIG_JFFS2_CMODE_NONE is not set
# CONFIG_JFFS2_CMODE_PRIORITY is not set
# CONFIG_JFFS2_CMODE_SIZE is not set
CONFIG_JFFS2_CMODE_FAVOURLZO=y
# CONFIG_UBIFS_FS is not set
CONFIG_CRAMFS=y
CONFIG_VXFS_FS=y
CONFIG_MINIX_FS=y
# CONFIG_OMFS_FS is not set
CONFIG_HPFS_FS=y
CONFIG_QNX4FS_FS=y
CONFIG_ROMFS_FS=y
CONFIG_SYSV_FS=y
CONFIG_UFS_FS=y
CONFIG_UFS_FS_WRITE=y
CONFIG_UFS_DEBUG=y
CONFIG_NETWORK_FILESYSTEMS=y
CONFIG_NFS_FS=m
CONFIG_NFS_V3=y
CONFIG_NFS_V3_ACL=y
CONFIG_NFS_V4=y
CONFIG_NFSD=m
CONFIG_NFSD_V2_ACL=y
CONFIG_NFSD_V3=y
CONFIG_NFSD_V3_ACL=y
CONFIG_NFSD_V4=y
CONFIG_LOCKD=m
CONFIG_LOCKD_V4=y
CONFIG_EXPORTFS=m
CONFIG_NFS_ACL_SUPPORT=m
CONFIG_NFS_COMMON=y
CONFIG_SUNRPC=m
CONFIG_SUNRPC_GSS=m
CONFIG_SUNRPC_XPRT_RDMA=m
CONFIG_RPCSEC_GSS_KRB5=m
CONFIG_RPCSEC_GSS_SPKM3=m
CONFIG_SMB_FS=m
# CONFIG_SMB_NLS_DEFAULT is not set
CONFIG_CIFS=m
# CONFIG_CIFS_STATS is not set
CONFIG_CIFS_WEAK_PW_HASH=y
# CONFIG_CIFS_UPCALL is not set
# CONFIG_CIFS_XATTR is not set
# CONFIG_CIFS_DEBUG2 is not set
# CONFIG_CIFS_EXPERIMENTAL is not set
CONFIG_NCP_FS=m
CONFIG_NCPFS_PACKET_SIGNING=y
CONFIG_NCPFS_IOCTL_LOCKING=y
CONFIG_NCPFS_STRONG=y
CONFIG_NCPFS_NFS_NS=y
CONFIG_NCPFS_OS2_NS=y
# CONFIG_NCPFS_SMALLDOS is not set
CONFIG_NCPFS_NLS=y
CONFIG_NCPFS_EXTRAS=y
CONFIG_CODA_FS=m
CONFIG_AFS_FS=m
# CONFIG_AFS_DEBUG is not set
CONFIG_9P_FS=m

#
# Partition Types
#
CONFIG_PARTITION_ADVANCED=y
CONFIG_ACORN_PARTITION=y
CONFIG_ACORN_PARTITION_CUMANA=y
CONFIG_ACORN_PARTITION_EESOX=y
CONFIG_ACORN_PARTITION_ICS=y
CONFIG_ACORN_PARTITION_ADFS=y
CONFIG_ACORN_PARTITION_POWERTEC=y
CONFIG_ACORN_PARTITION_RISCIX=y
CONFIG_OSF_PARTITION=y
CONFIG_AMIGA_PARTITION=y
CONFIG_ATARI_PARTITION=y
CONFIG_MAC_PARTITION=y
CONFIG_MSDOS_PARTITION=y
CONFIG_BSD_DISKLABEL=y
CONFIG_MINIX_SUBPARTITION=y
CONFIG_SOLARIS_X86_PARTITION=y
CONFIG_UNIXWARE_DISKLABEL=y
CONFIG_LDM_PARTITION=y
CONFIG_LDM_DEBUG=y
CONFIG_SGI_PARTITION=y
CONFIG_ULTRIX_PARTITION=y
CONFIG_SUN_PARTITION=y
CONFIG_KARMA_PARTITION=y
CONFIG_EFI_PARTITION=y
CONFIG_SYSV68_PARTITION=y
CONFIG_NLS=y
CONFIG_NLS_DEFAULT="cp437"
CONFIG_NLS_CODEPAGE_437=y
CONFIG_NLS_CODEPAGE_737=m
CONFIG_NLS_CODEPAGE_775=m
CONFIG_NLS_CODEPAGE_850=m
CONFIG_NLS_CODEPAGE_852=m
CONFIG_NLS_CODEPAGE_855=m
CONFIG_NLS_CODEPAGE_857=m
CONFIG_NLS_CODEPAGE_860=m
CONFIG_NLS_CODEPAGE_861=m
CONFIG_NLS_CODEPAGE_862=m
CONFIG_NLS_CODEPAGE_863=m
CONFIG_NLS_CODEPAGE_864=m
CONFIG_NLS_CODEPAGE_865=m
CONFIG_NLS_CODEPAGE_866=m
CONFIG_NLS_CODEPAGE_869=m
CONFIG_NLS_CODEPAGE_936=m
CONFIG_NLS_CODEPAGE_950=m
CONFIG_NLS_CODEPAGE_932=m
CONFIG_NLS_CODEPAGE_949=m
CONFIG_NLS_CODEPAGE_874=m
CONFIG_NLS_ISO8859_8=m
CONFIG_NLS_CODEPAGE_1250=m
CONFIG_NLS_CODEPAGE_1251=m
CONFIG_NLS_ASCII=m
CONFIG_NLS_ISO8859_1=m
CONFIG_NLS_ISO8859_2=m
CONFIG_NLS_ISO8859_3=m
CONFIG_NLS_ISO8859_4=m
CONFIG_NLS_ISO8859_5=m
CONFIG_NLS_ISO8859_6=m
CONFIG_NLS_ISO8859_7=m
CONFIG_NLS_ISO8859_9=m
CONFIG_NLS_ISO8859_13=m
CONFIG_NLS_ISO8859_14=m
CONFIG_NLS_ISO8859_15=m
CONFIG_NLS_KOI8_R=m
CONFIG_NLS_KOI8_U=m
CONFIG_NLS_UTF8=y
CONFIG_DLM=m
CONFIG_DLM_DEBUG=y


```I use SATA hard drives, so it seems to me that my configuration should be fine. 

When I run "ls /sbin/", one of the files listed is init - so I know it's there, and the kernel looks there for it, even if I don't specify the init=/sbin/init option.

Any ideas on what I can do to fix this? 
I don't need my keyboard LEDs to sync, but I do need my kernel to sync. 
I need to flip-flop the situation...

---

### Post by Crafty Kisses on 2008-11-02
This type of kernel panic usually comes up if you do not have the correct file system  support. You might have mounted a wrong partition, you could have also left something out of your kernel configuration. What are the results of this command? ```
sudo fdisk -l
```

---

### Post by computer_freak_8 on 2008-11-02
> **Codename said:**
> This type of kernel panic usually comes up if you do not have the correct file system  support. You might have mounted a wrong partition, you could have also left something out of your kernel configuration. What are the results of this command? ```
sudo fdisk -l
```

I am aware of these things, hence why I posted the information from the files and mentioned why I was posting it.

Nonetheless, here is the result:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea188

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   b  W95 FAT32
/dev/sda2           59343       60801    11719417+  82  Linux swap / Solaris
/dev/sda3            2433       59342   457129575    5  Extended
/dev/sda5           40002       43825    30716248+  83  Linux
/dev/sda6           43826       47012    25599546   83  Linux
/dev/sda7            2433       14954   100582902   83  Linux
/dev/sda8           14955       27476   100582933+  83  Linux
/dev/sda9           27477       40001   100607031   83  Linux
/dev/sda10          47013       59342    99040693+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6522269e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10241406    7  HPFS/NTFS
/dev/sdb2            1276        8747    60018840    6  FAT16
/dev/sdb3            8748       22898   113667907+   7  HPFS/NTFS
/dev/sdb4           22899       38913   128640487+   5  Extended
/dev/sdb5           22899       27360    35840983+  83  Linux
/dev/sdb6           27361       29527    17406396   83  Linux

```

---

### Post by computer_freak_8 on 2008-11-02
Oh, one more thing:
I have seen that, on certain posts on the Internet, the problem was caused because the user ran out of disk space. I had checked my free space (via Gnome System Monitor) and found that I have 21.4GiB free. So there goes *that* particular possibility.

---

### Post by Crafty Kisses on 2008-11-02
First, I was just letting you know, but anyway go into the Grub command line and do the following:
```
root (<tab>)
```
Where tab is you should have a list of drives, if Grub doesn't list the drive or partition where you think your **/boot** directory or partition is, you need to either assume Grub knows better or you need to check your hardware. You then need to press the character that corresponds to the drive/partition where your /boot directory is located, you must repeat this step until you get something like this:
```
root (hdx,y)
```
You probably already know Grub counts drives and partitions starting with 0 for the first primary partition and 4 for the first extended partition. Seeing as you have a lot of drives, you should probably do:
```
kernel /vmlin<tab>
```
You may want to add the following to the kernel filename (same line):
```
ro
```That will make sure that the filesystems will be mounted at first. In most cases once you hit "tab" Grub should complete the filename. You then need to tell Grub where your root partition is located, so it should look something like this: ```
kernel /vmlinuz-kernelname ro root=/dev/hda4
``` You obviously need to substitute your own information and replace **/hda4 **with your information. Then your next step would be entering this command:
```
initrd /initrd<tab>
```
After that you might be able to boot, so after you've done that type:
```
boot
```
Remember this will all depend on if you have a separate boot partition or not, I just guessed and made it so this would work if you **DID** have a separate boot partition. I've compiled tons of kernels, and I'm not sure why you're having this issue, the root of the problem obviously lies within the drives and partitions. Here is a great thread over at "LinuxForums" a bit more in depth then what I did: [http://www.linuxforums.org/forum/linux-kernel/19267-kernel-panic-no-init-found.html](http://www.linuxforums.org/forum/linux-kernel/19267-kernel-panic-no-init-found.html)

---

### Post by computer_freak_8 on 2008-11-02
> **Codename said:**
> First, I was just letting you know, ...
Yes, I re-read my post:> **computer_freak_8 said:**
> I am aware of these things, hence why I posted the information from the files and mentioned why I was posting it.And I realized that it may have sounded a bit rude. Sorry about this; it was not my intention. You were just trying to help, and I greatly appreciate that.

As for:> **Codename said:**
> 
Remember this will all depend on if you have a separate boot partition or not, I just guessed and made it so this would work if you **DID** have a separate boot partition.Unfortunately, I do not have a separate/dedicated boot partition. The one containing the installation I use (the one with the problematic kernel) is the boot partition for all my other operating systems (which are all Linux).

The thing that really confuses me about this is that there are only three differences:
1. New kernel, compiled by me -versus- Ubuntu kernel
2. New initial ramdisk, generated by me -versus- Ubuntu ramdisk
3. Not working -versus- Working just fine
(All of the above are respective of each other.)

Any ideas as to *why*? It's driving me nuts...


Thanks again,
computer_freak_8

---

### Post by Crafty Kisses on 2008-11-02
In the case that you don't have a separate boot partition, it would just change a little bit, so for example if you have had a separate boot partition it would look like this:
```
initrd /initrd<tab>
```
As you stated you do not have a separate boot partition, so it would look like this:
```
initrd  /boot/initrd<tab>
```
This would also be true for the "**kernel /vm**" line.

---

### Post by computer_freak_8 on 2008-11-02
I'm still a bit confused, but that's okay. I just had a thought: try crossing my grub settings. I'm going to reboot a couple of times after this post, and I'll try your idea and my idea, and let you know what happened.

---

### Post by Yashiro on 2008-11-03
> # mkinitramfs -o initrd.img-2.6.27.4 2.6.27.4
Actually succeeds?

---

### Post by computer_freak_8 on 2008-11-03
Okay, sorry for the delay, forgot I had to get ready for bed so I could get up in time for school.

As for:
> **Yashiro said:**
> Actually succeeds?Unless I made typographical error in my post, yes, it does succeed. 

Okay, I tried using "find" and the TAB key to boot from grub manually; same error as before.
I tried the new kernel with the Ubuntu ramdisk; same error.
I tried the Ubuntu kernel with the new ramdisk; failed with BusyBox after a line that said something like "Begin. Mounting root partition..."

My next idea I have is to try the same thing, only using the -21 and -19 versions of the Ubuntu kernel and ramdisk, instead of the custom/Ubuntu combination, just to see what happens, so I can tell whether my ramdisk is bad.


Thanks,
computer_freak_8

---

### Post by Crafty Kisses on 2008-11-03
I'm going to assume your Ubuntu root partition is at /dev/sda1 and that that is an ext3 volume. Boot the LiveCD and **chroot** your install.
```
mkdir /media/ubuntu
mount -t ext3 -o defaults,rw /dev/sda1 /media/ubuntu
chroot /media/ubuntu
```
Remember substitute your own information.

---

### Post by computer_freak_8 on 2008-11-03
> **Codename said:**
> Boot the LiveCD and **chroot** your install.

And then what? What do I do to fix the kernel panic?

---

### Post by Crafty Kisses on 2008-11-03
After you chroot your install through the LiveCD and ran the commands I gave you, boot back into Ubuntu and see if you can continue compiling your kernel. My bet is that **/bin/insmod** is missing on your initrd or the initrd-image is corrupt for some reason. I'm not sure if you have tried this either, installing ext3 in your kernel. This could actually get you passed this error, try the following:
```
make menuconfig
make depend
make
make install

```
Remember to select ext3 from the list.

---

### Post by computer_freak_8 on 2008-11-04
> **Codename said:**
> After you chroot your install through the LiveCD and ran the commands I gave you, boot back into Ubuntu and see if you can continue compiling your kernel. My bet is that **/bin/insmod** is missing on your initrd or the initrd-image is corrupt for some reason. I'm not sure if you have tried this either, installing ext3 in your kernel. This could actually get you passed this error, try the following:
```
make menuconfig
make depend
make
make install

```
Remember to select ext3 from the list.

Okay, I'm confused. First off, the commands you previously gave me were for booting from the GRUB command line. Using "chroot", this is not possible, since the (live) operating system is already loaded. Besides, we have already verified that I have the correct file names.
As for selecting ext3 support, I already did:> **computer_freak_8 said:**
> 
#
# File systems
#
CONFIG_EXT2_FS=y
CONFIG_EXT2_FS_XATTR=y
CONFIG_EXT2_FS_POSIX_ACL=y
CONFIG_EXT2_FS_SECURITY=y
CONFIG_EXT2_FS_XIP=y
CONFIG_FS_XIP=y
CONFIG_EXT3_FS=y
CONFIG_EXT3_FS_XATTR=y
CONFIG_EXT3_FS_POSIX_ACL=y
CONFIG_EXT3_FS_SECURITY=y
CONFIG_EXT4DEV_FS=y
CONFIG_EXT4DEV_FS_XATTR=y
CONFIG_EXT4DEV_FS_POSIX_ACL=y
CONFIG_EXT4DEV_FS_SECURITY=y
CONFIG_JBD=y
CONFIG_JBD_DEBUG=y
CONFIG_JBD2=y
CONFIG_JBD2_DEBUG=y
CONFIG_FS_MBCACHE=y
CONFIG_REISERFS_FS=y
CONFIG_REISERFS_CHECK=y
CONFIG_REISERFS_PROC_INFO=y
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y
CONFIG_JFS_FS=y
CONFIG_JFS_POSIX_ACL=y
CONFIG_JFS_SECURITY=y
CONFIG_JFS_DEBUG=y
CONFIG_JFS_STATISTICS=y
CONFIG_FS_POSIX_ACL=y
CONFIG_XFS_FS=y
CONFIG_XFS_QUOTA=y
CONFIG_XFS_POSIX_ACL=y
CONFIG_XFS_RT=y
# CONFIG_XFS_DEBUG is not set
CONFIG_GFS2_FS=y
CONFIG_GFS2_FS_LOCKING_DLM=m
CONFIG_OCFS2_FS=y
CONFIG_OCFS2_FS_O2CB=y
CONFIG_OCFS2_FS_USERSPACE_CLUSTER=m
CONFIG_OCFS2_FS_STATS=y
CONFIG_OCFS2_DEBUG_MASKLOG=y
CONFIG_OCFS2_DEBUG_FS=y
CONFIG_DNOTIFY=y
CONFIG_INOTIFY=y
CONFIG_INOTIFY_USER=y
CONFIG_QUOTA=y
CONFIG_QUOTA_NETLINK_INTERFACE=y
CONFIG_PRINT_QUOTA_WARNING=y
CONFIG_QFMT_V1=y
CONFIG_QFMT_V2=y
CONFIG_QUOTACTL=y
CONFIG_AUTOFS_FS=y
CONFIG_AUTOFS4_FS=y
CONFIG_FUSE_FS=y
CONFIG_GENERIC_ACL=y

The above is from my original post. 

Any other ideas, or am I missing something? Sorry to be a pain, I just don't quite get it...:confused:

---------------------

Pre-post edit: I just noticed your compiling commands are a bit different. I'll try those, and then post back. 


Thanks,
computer_freak_8

---

### Post by computer_freak_8 on 2008-11-04
I tried your commands for compiling the kernel; same error message as before.

After that, I tried every possible combination of the three kernels and three ramdisks. My conclusion is that I'm almost (but not quite) positive that the ramdisk is fine, and the kernel is somehow messed up. 

Are there any specific parameters I need to give to it that I'm not giving?

Another thought I had: Is the 2.6.27.4 kernel a development version, perhaps? I recall that the development versions use odd numbers, but I don't know if that's just for the major version, or if it applies so all minor revisions, too. Can someone shed some light on this? 

Note: I'm pretty sure I've got a stable kernel version; according to a link I found ([here]("http://www.thelinuxlink.net/lvlinux/resources/presentations/kernel/kernelcompksource.html")), I have a stable (not development) kernel. It the page I linked to accurate?

---

