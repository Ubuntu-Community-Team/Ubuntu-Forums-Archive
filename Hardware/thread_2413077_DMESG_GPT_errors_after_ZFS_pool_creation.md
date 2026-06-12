---
title: "DMESG GPT errors after ZFS pool creation"
date: 2019-02-20
forum: Hardware
---

### Post by qombi on 2019-02-20
Hello! I noticed these messages in DMESG after installing ZFS on linux from the repositories. Information in regards to distro, install steps and DMESG errors are below. I have a difficult time believing all three drives that I just added to a ZFS pool happen to be having I/O issues at the same time. I also scanned the drives with smartcl -t long and see no issues. I am hoping someone let me know if this is a known issue with ZFS pool creation, possibly the method I went about it, or indeed coincidentally all three drives are bad. Thanks! 

OS information:  (alternate installer)
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic

Install Steps:

parted
select /dev/sdd
mklabel GPT
parted
select /dev/sde
mklabel GPT
parted
select /dev/sdf
mklabel GPT

install zfsutils-linux
zpool create -o ashift=12 zp1 raidz1 /dev/sde /dev/sdf /dev/sdd


DMESG: 


 2053.777110] SPL: Loaded module v0.7.5-1ubuntu1
[ 2053.785371] znvpair: module license 'CDDL' taints kernel.
[ 2053.785374] Disabling lock debugging due to kernel taint
[ 2055.450274] ZFS: Loaded module v0.7.5-1ubuntu15, ZFS pool version 5000, ZFS filesystem version 5
[ 3876.607542]  sdd:
[ 3888.817021]  sde:
[ 3896.419329]  sdf:
[ 3914.860231] GPT:disk_guids don't match.
[ 3914.860238] GPT:partition_entry_array_crc32 values don't match: 0xf07aee04 != 0xab54d286
[ 3914.860240] GPT: Use GNU Parted to correct GPT errors.
[ 3914.860272]  sdd: sdd1 sdd9
[ 3914.947302]  sdd: sdd1 sdd9
[ 3915.599135] GPT:disk_guids don't match.
[ 3915.599142] GPT:partition_entry_array_crc32 values don't match: 0xf7a0b7c4 != 0xab54d286
[ 3915.599144] GPT: Use GNU Parted to correct GPT errors.
[ 3915.599175]  sde: sde1 sde9
[ 3915.706809]  sde: sde1 sde9
[ 3915.925204] GPT:disk_guids don't match.
[ 3915.925210] GPT:partition_entry_array_crc32 values don't match: 0x642ce7f8 != 0xab54d286
[ 3915.925212] GPT: Use GNU Parted to correct GPT errors.
[ 3915.925238]  sdf: sdf1 sdf9
[ 3916.082823]  sdf: sdf1 sdf9

---

