---
title: "Error mounting NTFS USB thumb drive"
date: 2012-04-13
forum: Hardware
---

### Post by r_avital on 2012-04-13
Hello all,

Here's the situation:

UBUNTU Lucid 10.04 LTS 64-Bit, PNY 64Gb USB thumb drive (ATTACHE) - formatted as NTFS (FAT32 won't support anything above 32Gb).  When inserting into USB port, I get the following error in a window:

Unable to mount ATTACHE
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdd': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


I've installed dmraid and looked at the documentation, but not sure where to go from there, and I'm not sure this is pertinent.

lsusb returns:Bus 001 Device 008: ID 090c:1000 Feiya Technology Corp. Flash Drive

I know "Bus 001" is good because other devices on it work fine, example:

Bus 001 Device 004: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09

I also know I've installed NTFS utilities on the system, but maybe something is missing?

Any input will be appreciated.

Thanks :)

---

### Post by oldfred on 2012-04-13
NTFS requires the PBR - partition boot sector to have a NTFS signature including the same size info as the partition table. It seems the signature may not be correct.

From Windows or a Windows repairCD/USB run chkdsk on the NTFS partition.

chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)


Only if that fails:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Rebuilding An NTFS Boot Sector On An NTFS Partition 
small 'system reserved' NTFS partition instead of the partition where windows was installed.

---

### Post by ahallubuntu on 2012-04-13
Here's a little secret: FAT32 can have much larger partitions than 32GB.  You can make a 64GB FAT32 partition if you want; I've had larger FAT32 partitions than that.

Windows ITSELF can't (won't) make partitions larger than that, but you can simply create one with Ubuntu using say Gparted.  Once you've formatted your FAT32 partition, you'll be able to use it as large as you wish with Windows, too, without any issues.  (One real hard limitation of FAT32: files can't be larger than about 4.1GB.)

(I don't remember the historical reason Windows refuses to make partitions larger than 32GB - could be incompatibility with older operating systems.  Google it if you are curious.)

So - I don't know if that's easier for you at this point, but if you can live with files under 4.1GB in size, FAT32 might be the path of least resistance for you.

---

