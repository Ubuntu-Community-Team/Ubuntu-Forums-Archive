---
title: "encrypted volume wont boot"
date: 2008-08-06
forum: General Help
---

### Post by fistcar on 2008-08-06
Hello,

When I installed 8.04 I decided to try out the encrypted disk option. The system was working fine for a week or two and today it would not boot.

I get:
Modprobe: error inserting padlock_sha/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-sha.ko no such device. 
After I enter the correct pass phrase.

Followed by errors like:
[ 1725.649762] ata3.00: status: { DRDY ERR }
[ 1725.649766] ata3.00: error: { UNC }
[ 1725.654293] ata3.00: configured for UDMA/100
[ 1725.654316] ata3: EH complete
[ 1729.656165] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1729.656178] ata3.00: BMDMA stat 0x25
[ 1729.656190] ata3.00: cmd c8/00:08:8e:a3:07/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 1729.656193] res 51/40:04:92:a3:07/00:00:00:00:00/e0 Emask 0x9 (media error)

I pulled these examples out of syslog.


I tried using the rescue kernel and get the same result. I tried using the rescue broken system from the install disk. It fails to open a shell for me. 

I used a live CD and tried to mount the drive:
sudo su
apt-get install lvm2 cryptsetup
mkdir /media/test
modprobe dm-crypt
cryptsetup luksOpen /dev/sda5 test
"entered password"
"command successful"
vgchange -ay
"2 logical volumes activate"
mount /dev/workywork/root /media/test
mount: wrong fs type, bad option, bad superblock on /dev/mapper/workywork-root, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail  or so
mount -t ext3 -o defaults /dev/workywork/root /media/test
mount: wrong fs type, bad option, bad superblock on /dev/mapper/workywork-root, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail  or so

I checked out syslog and see:

[ 1741.676648] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1741.676661] ata3.00: BMDMA stat 0x25
[ 1741.676672] ata3.00: cmd c8/00:08:8e:a3:07/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 1741.676675] res 51/40:04:92:a3:07/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 1741.676681] ata3.00: status: { DRDY ERR }
[ 1741.676685] ata3.00: error: { UNC }
[ 1741.681166] ata3.00: configured for UDMA/100
[ 1741.681190] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1741.681197] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1741.681207] Descriptor sense data with sense descriptors (in hex):
[ 1741.681212] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1741.681231] 00 07 a3 92
[ 1741.681239] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1741.681252] end_request: I/O error, dev sda, sector 500626
[ 1741.681288] ata3: EH complete
[ 1741.681311] EXT3-fs: can't read group descriptor 12
[ 1741.682920] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 1741.682946] sd 2:0:0:0: [sda] Write Protect is off
[ 1741.682952] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1741.682987] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1741.683025] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 1741.683045] sd 2:0:0:0: [sda] Write Protect is off
[ 1741.683050] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1741.683084] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

I don't know where to go from here. Any help is greatly appreciated.

---

### Post by fistcar on 2008-08-07
bump

---

