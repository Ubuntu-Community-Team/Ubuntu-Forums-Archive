---
title: "Dell Perc 5/iR - seems to be disconnecting drives"
date: 2014-06-13
forum: Hardware
---

### Post by Darren_Parr on 2014-06-13
Hi

Ive got a strange problem. This is a desktop machine which I use for media etc. I have 4 x 2TB drives plugged into a Dell raid card in a non raid configuration. During rsync commands or cp commands, the disks can become detached, but only after several hours.

badblocks shows nothing is wrong and this is not happening all of the time. It almost feels like a driver issue.

So I have devices sdb,sdc,sdd and sde which map to these disks. One of these drives has 2 x 1TB partitions and the others are 2TB partitions. On disconnect its as though ubuntu creates a complete;y different special device (say /dev/sdf). Last night during a backup it sell over on the 2 x 1TB drives and they both disappeared. On cd'ing to the mount point you just get ls : input/output error. An attempt to remount them works fine (only the device has switched over).

Heres the output from dmesg. The device is mounted on /dev/sdf1 and /dev/sdf2. It switches back to /dev/sdb as you can see.

 [47311.058491] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 0, phy 0, sas_addr 0x1221000000000000
[47311.073300] scsi 6:0:13:0: Direct-Access     ATA      WDC WD20EARX-00P AB51 PQ: 0 ANSI: 5
[47311.075046] sd 6:0:13:0: Attached scsi generic sg4 type 0
[47311.077388] sd 6:0:13:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[47311.104527] sd 6:0:13:0: [sdb] Write Protect is off
[47311.104531] sd 6:0:13:0: [sdb] Mode Sense: 73 00 00 08
[47311.118927] sd 6:0:13:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[47311.230214]  sdb: sdb1 sdb2
[47311.316190] sd 6:0:13:0: [sdb] Attached SCSI disk
[65905.636624] EXT4-fs error (device sdf2): ext4_find_entry:1309: inode #2: comm sh: reading directory lblock 0

# lspci -v

02:08.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068 PCI-X Fusion-MPT SAS (rev 01)
        Subsystem: Dell SAS 5/iR Adapter RAID Controller
        Flags: bus master, 66MHz, medium devsel, latency 72, IRQ 16
        I/O ports at e000 [disabled] [size=256]
        Memory at f7d10000 (64-bit, non-prefetchable) [size=16K]
        Memory at f7d00000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at f7c00000 [disabled] [size=1M]
        Capabilities: [50] Power Management version 2
        Capabilities: [98] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [68] PCI-X non-bridge device
        Capabilities: [b0] MSI-X: Enable- Count=1 Masked-
        Kernel driver in use: mptsas


Any ideas?

Darren

---

### Post by tgalati4 on 2014-06-13
I would clean and reseat the cables connecting the PERC card and hard drives.  Update the Dell and RAID BIOS to the latest.  Replace the battery on the PERC card if you have one.  Burn a copy of Dell's diagnostics onto a CD and run through them.  Install *phoronix-test-suite *and run some disk-based stress tests to make sure the drives and PERC card are working before you put the machine back into production.

Ignore everything I have said above.  Don't use green drives with a PERC RAID card.

---

### Post by Darren_Parr on 2014-06-14
Thanks. Ive done that. I'll keep an eye on it.

---

