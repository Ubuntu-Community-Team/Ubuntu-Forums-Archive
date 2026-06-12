---
title: "SATA drive not recognized on Ubuntu Server 15.10"
date: 2016-02-12
forum: Hardware
---

### Post by williambertram on 2016-02-12
Good afternoon,

First, the title should be "eSATA drive not recognized on Ubuntu Server 15.10", not "SATA..."  Sorry about that.

I've been Googling and trying things but not making any progress so thought I'd try here.

I have a Dell Latitude E4300 with an integrated eSATA port running Ubuntu Server 15.10.  When I plug an eSATA drive into it, it is not detected by the OS.  If I type fdisk -l it is not displayed.  I have powered the laptop completely off, powered up the eSATA drive and connected the eSATA cable, then powered on the laptop with no luck.  I have confirmed the drive is fully functional in Windows 8 on the same laptop.  I have confirmed that eSATA is enabled in the bios, and SATA mode is IRRT.  I am booting from an internal SATA drive, and that is working just fine.  Tried multiple reboots of the laptop, and power cycling the drive as well with the drive powered on and SATA cable connected before the laptop is powered up.  I have also tried connecting the drive "hot", while the OS is running but no luck there either.

I have tried rescan-scsi-bus.sh, and it says 0 drives added or removed, and fdisk -l still does not show the drive.

The hard drives are Seagate 2TB 5400 RPM drives.  I'm using an eSATA to SATA cable, and a separate power source that plugs into the wall for the drive.

I have also tried a different cable, and a different identical drive with no luck.  I have also verified that Ubuntu Server 15.10 can see the drive if it is connected to a desktop as SATA (not eSATA).

At this point, my theory is that possibly IRRT mode might be the problem, however I really don't want to re-install the OS to switch over to ATA mode.  I read one post that hinted that possibly the Intel chipset drivers might be needed for the eSATA to work, but I looked for over an hour and was not able to find how to do that, or which driver might be needed.

This is for a home server, so it's not mission critical, and if need be I can at some point rebuild the server in ATA mode if need be.  It would be nice if there is something easy I'm just missing though that a guru can point out.  :)


Thank you!

Here is my output from rescan-scsi-bus.  Note that the two drives listed in the output are not the eSATA drive I am trying to connect.  One of them is an internal SATA drive, and the other is connected via USB.  The eSATA drive would be a third drive that is not showing up here.


```
administrator@srv01:~$ sudo rescan-scsi-bus
[sudo] password for administrator:
/sbin/rescan-scsi-bus: line 592: [: 1.43: integer expression expected
Host adapter 0 (usb-storage) found.
Host adapter 1 (ahci) found.
Host adapter 2 (ahci) found.
Host adapter 3 (ahci) found.
Host adapter 4 (ahci) found.
Host adapter 5 (ahci) found.
Host adapter 6 (ahci) found.
Scanning SCSI subsystem for new devices
Scanning host 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 0 0 0 0 ...
OLD: Host: scsi0 Channel: 00 Id: 00 Lun: 00
      Vendor: Seagate  Model: FreeAgent        Rev: 0132
      Type:   Direct-Access                    ANSI SCSI revision: 04
Scanning for device 0 0 0 0 ...
OLD: Host: scsi0 Channel: 00 Id: 00 Lun: 00
      Vendor: Seagate  Model: FreeAgent        Rev: 0132
      Type:   Direct-Access                    ANSI SCSI revision: 04
Scanning for device 0 0 0 0 ...
OLD: Host: scsi0 Channel: 00 Id: 00 Lun: 00
      Vendor: Seagate  Model: FreeAgent        Rev: 0132
      Type:   Direct-Access                    ANSI SCSI revision: 04
Scanning for device 0 0 0 0 ...
OLD: Host: scsi0 Channel: 00 Id: 00 Lun: 00
      Vendor: Seagate  Model: FreeAgent        Rev: 0132
      Type:   Direct-Access                    ANSI SCSI revision: 04
Scanning host 1 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 1 0 0 0 ...
OLD: Host: scsi1 Channel: 00 Id: 00 Lun: 00
      Vendor: ATA      Model: ST9160412ASG     Rev: SDM1
      Type:   Direct-Access                    ANSI SCSI revision: 05
Scanning host 2 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 2 0 0 0 ...
OLD: Host: scsi2 Channel: 00 Id: 00 Lun: 00
      Vendor: TSSTcorp Model: DVD+-RW TS-U633F Rev: D500
      Type:   CD-ROM                           ANSI SCSI revision: 05
Scanning host 3 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 4 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 5 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 6 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
0 new device(s) found.
0 device(s) removed.
```

Here is fdisk -l | grep "/dev".  The drive is not showing up here either.

```
administrator@srv01:~$ sudo fdisk -l | grep "/dev"
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 312580095 312078338 148.8G  5 Extended
/dev/sda5       501760 312580095 312078336 148.8G 8e Linux LVM
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
/dev/sdb1          63 3907024064 3907024002  1.8T  7 HPFS/NTFS/exFAT
Disk /dev/mapper/srv01--vg-root: 144.9 GiB, 155537375232 bytes, 303783936 sectors
Disk /dev/mapper/srv01--vg-swap_1: 4 GiB, 4244635648 bytes, 8290304 sectors
```

Here is dmesg | grep "sd":

```
administrator@srv01:~$ dmesg | grep "sd"
[    2.518310] sdhci: Secure Digital Host Controller Interface driver
[    2.528475] sdhci: Copyright(c) Pierre Ossman
[    2.710377] sdhci-pci 0000:02:01.1: SDHCI controller found [1180:0822] (rev 2 2)
[    2.731165] sdhci-pci 0000:02:01.1: No vmmc regulator found
[    2.731166] sdhci-pci 0000:02:01.1: No vqmmc regulator found
[    3.376439] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    3.376560] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149  GiB)
[    3.376649] sd 1:0:0:0: [sda] Write Protect is off
[    3.376675] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.376743] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, does n't support DPO or FUA
[    3.407199]  sda: sda1 sda2 < sda5 >
[    3.407631] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.605240] sd 0:0:0:0: Attached scsi generic sg1 type 0
[    3.605730] sd 0:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1. 81 TiB)
[    3.606497] sd 0:0:0:0: [sdb] Write Protect is off
[    3.606537] sd 0:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[    3.607244] sd 0:0:0:0: [sdb] No Caching mode page found
[    3.607284] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[    3.611402]  sdb: sdb1
[    3.615254] sd 0:0:0:0: [sdb] Attached SCSI disk
[   14.458258] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsyste m
[   14.475692] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
```

Here are the last 50 lines of dmesg:

```
administrator@srv01:~$ dmesg | tail --lines=50
[   11.730956] input: HDA Intel Dock Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.731030] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   11.731100] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   11.799660] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.799664] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.799666] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.799668] iwlwifi 0000:0c:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   11.799770] iwlwifi 0000:0c:00.0: L1 Enabled - LTR Disabled
[   11.849276] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.868239] iwlwifi 0000:0c:00.0 wlp12s0: renamed from wlan0
[   12.347670] cfg80211: World regulatory domain updated:
[   12.347675] cfg80211:  DFS Master region: unset
[   12.347676] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   12.347679] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   12.347681] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   12.347683] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   12.347686] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   12.347689] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   12.347691] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   12.347693] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   12.347695] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   13.791782] Adding 4145148k swap on /dev/mapper/srv01--vg-swap_1.  Priority:-1 extents:1 across:4145148k FS
[   14.458258] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   14.475692] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   16.322703] audit: type=1400 audit(1455296727.588:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=488 comm="apparmor_parser"
[   16.322713] audit: type=1400 audit(1455296727.588:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=488 comm="apparmor_parser"
[   16.322720] audit: type=1400 audit(1455296727.588:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=488 comm="apparmor_parser"
[   16.322727] audit: type=1400 audit(1455296727.588:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=488 comm="apparmor_parser"
[   16.428603] audit: type=1400 audit(1455296727.696:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=488 comm="apparmor_parser"
[   16.580151] ifquery[493]: segfault at 1 ip 0000000000403187 sp 00007ffc15229640 error 4 in ifup[400000+d000]
[   16.952206] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   18.460892] e1000e: enp0s25 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   18.461003] e1000e 0000:00:19.0 enp0s25: 10/100 speed: disabling TSO
[   18.461037] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[  571.214386] ata5: hard resetting link
[  571.532186] ata5: SATA link down (SStatus 0 SControl 300)
[  571.532212] ata5: EH complete
[  571.672773] ata6: hard resetting link
[  571.992126] ata6: SATA link down (SStatus 0 SControl 300)
[  571.992153] ata6: EH complete
[  601.114895] dell_wmi: Unknown WMI event type 0x11: 0xffd0
[  601.114896] dell_wmi: Unknown WMI event type 0x11: 0xffd1
[  601.114897] dell_wmi: Unknown WMI event type 0x11: 0xffd1
[  601.114898] dell_wmi: Unknown WMI event type 0x11: 0xffd0
[10080.817369] ata5: hard resetting link
[10081.136327] ata5: SATA link down (SStatus 0 SControl 300)
[10081.136353] ata5: EH complete
[10081.278173] ata6: hard resetting link
[10081.596301] ata6: SATA link down (SStatus 0 SControl 300)
[10081.596326] ata6: EH complete
```

---

### Post by sudodus on 2016-02-12
What is this drive?

```
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
/dev/sdb1 63 3907024064 3907024002 1.8T 7 HPFS/NTFS/exFAT
Disk /dev/mapper/srv01--vg-root: 144.9 GiB, 155537375232 bytes, 303783936 sectors
Disk /dev/mapper/srv01--vg-swap_1: 4 GiB, 4244635648 bytes, 8290304 sectors
```

-o-

I am using eSATA and have no problems (in desktop computers as well as in Toshiba and HP laptops), but I don't know about IRRT.

It should be straightforward to connect a drive like that. (I tried it myself right now and it works with that kind of cable as you describe (eSATA - SATA) and a 'naked' SATA drive).

I connect an eSATA drive (an SSD or HDD in an external box) to an eSATA port with an eSATA - eSATA cable.

---

### Post by williambertram on 2016-02-13
That is a USB drive plugged into the USB port.  Not the eSATA drive I'm trying to use.  I agree that plugging in an eSATA drive would normally be straightforward, but there is no indication that the OS is detecting the drive that I can see.  At this point I'm assuming that either A) This particular eSATA port is not supported, and / or needs a proprietary chipset driver installed, which I do not know how to do currently.  Or B) The SATA "mode" configured in the bios might need to be changed to ATA to work in this OS.  These are just guesses though, as I'm kind of out of ideas.  For lack of a better solution, or until I figure it out I'm just going to buy a USB hub and connect it that way since the laptop only has one USB port.  YES there is probably better hardware in existence for a home server, this is just all I have available, and it's doing the job I want it to.  :)  Thanks again for the help.

---

