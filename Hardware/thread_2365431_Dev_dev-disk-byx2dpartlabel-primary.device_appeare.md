---
title: "Dev dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths"
date: 2017-07-06
forum: Hardware
---

### Post by robertzito on 2017-07-06
I was looking at my syslog and saw the message below about the primary device, I did some searching on this but cant find anything...

Can anyone help? 


```
systemd[1]: dev-disk-by\x2dpartlabel-primary.device: Dev dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1d.0/0000:6f:00.0/nvme/nvme0/nvme0n1/nvme0n1p2 and /sys/devices/pci0000:00/0000:00:17.0/ata3/host2/target2:0:0/2:0:0:0/block/sda/sda1
```

---

### Post by Bashing-om on 2017-07-06
robertzito; Hummm ..

We have:
> 
/nvme/nvme0/nvme0n1/nvme0n1p2 and 
host2/target2:0:0/2:0:0:0/block/sda/sda1

associated to the same PCI;
Maybe a mounting issue ??

Let's take a look at what is set for mounting at boot up.
Post back the output of terminal commands:
```

sudo blkid
sudo parted -l
cat /etc/fstab
cat /proc/mounts

```

see what we can do to
[INDENT][INDENT]get the ducks all in a row
[/INDENT][/INDENT]

---

### Post by robertzito on 2017-07-06
Here you go, thanks for taking the time to help

Output of blkid
```
/dev/nvme0n1p1: LABEL="EFI" UUID="F0D7-0908" TYPE="vfat" PARTLABEL="primary" PARTUUID="09de4362-0bda-4be8-a9f0-9da22de5b651"
/dev/nvme0n1p2: LABEL="Ubuntu" UUID="8b0f7c60-7c63-4916-ac50-793f88e90f97" TYPE="ext4" PARTLABEL="primary" PARTUUID="126f6138-2e11-4bf3-9029-868a26e990a4"
/dev/nvme0n1p3: UUID="5054b842-d8d7-4d4c-8539-76b7858de7ed" TYPE="swap" PARTLABEL="primary" PARTUUID="66307608-0eb3-4fe3-b26f-742b743f251d"
/dev/sda1: LABEL="ExtraDrive1" UUID="9b802392-fb1a-46d2-bb7a-11cb08da2440" TYPE="ext4" PARTLABEL="primary" PARTUUID="79e8a857-7536-4c83-9323-34c9b8852fe3"
/dev/sdb1: LABEL="disk" UUID="ed0ba56d-f01c-4e9e-91ca-a2db5758b934" TYPE="ext4" PARTUUID="0e36403d-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/nvme0n1: PTUUID="d17d44b5-dc44-492a-b6ac-bb57cd217cdf" PTTYPE="gpt"

```
 sudo parted -l
```
Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
```
```

# <file system>  <mount point>  <type>  <options>  <dump>  <pass>

# /dev/nvme0n1p2
UUID=8b0f7c60-7c63-4916-ac50-793f88e90f97  /  ext4  discard,noatime,errors=remount-ro  0  1

# /dev/nvme0n1p1
#UUID=F0D7-0908  /boot/efi  vfat  umask=0077  0  1

# /dev/nvme0n1p3
UUID=5054b842-d8d7-4d4c-8539-76b7858de7ed  none  swap  sw  0  0
UUID=F0D7-0908	/boot/efi	vfat	defaults	0	1

#Plex external mont
#UUID=26f2f3e4-3bec-4a41-9537-a02191244483   /media/rzito/ExtraDrive1/Media_2 etx4    0   0
#UUID=26f2f3e4-3bec-4a41-9537-a02191244483	/home/rzito/Multimedia ext4	00

# Mount Extra1 (ext4) at /disks/media3 for Plex
UUID=9b802392-fb1a-46d2-bb7a-11cb08da2440   /disks/ExtraDrive1  ext4    defaults,auto,rw,nofail 0   1
UUID=ed0ba56d-f01c-4e9e-91ca-a2db5758b934   /disks/ExtraDrive2  ext4    defaults,auto,rw,nofail 0   1
```


```

Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1000GB  1000GB  ext4         primary


Model: ATA ST2000LM007-1R81 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4


Model: Unknown (unknown)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name     Flags
 1      1049kB  538MB  537MB   fat32           primary  boot, esp
 2      538MB   508GB  507GB   ext4            primary
[B] 3      508GB   512GB  4295MB  linux-swap(v1)  primary
```

```
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,nosuid,relatime,size=32938504k,nr_inodes=8234626,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=6592768k,mode=755 0 0
/dev/nvme0n1p2 / ext4 rw,noatime,discard,errors=remount-ro,data=ordered 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /sys/fs/cgroup tmpfs rw,mode=755 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
efivarfs /sys/firmware/efi/efivars efivarfs rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
cgroup /sys/fs/cgroup/pids cgroup rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset,clone_children 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=12357 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
mqueue /dev/mqueue mqueue rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/loop1 /snap/hexchat/17 squashfs ro,nodev,relatime 0 0
/dev/loop0 /snap/core/2312 squashfs ro,nodev,relatime 0 0
/dev/loop2 /snap/core/1689 squashfs ro,nodev,relatime 0 0
/dev/nvme0n1p1 /boot/efi vfat rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0
/dev/sda1 /disks/ExtraDrive1 ext4 rw,relatime,data=ordered 0 0
cgmfs /run/cgmanager/fs tmpfs rw,relatime,size=100k,mode=755 0 0
/dev/sdb1 /disks/ExtraDrive2 ext4 rw,relatime,data=ordered 0 0
/dev/nvme0n1p2 /var/lib/docker/aufs ext4 rw,noatime,discard,errors=remount-ro,data=ordered 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=6592768k,mode=700,uid=1000,gid=1000 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
```

---

### Post by Bashing-om on 2017-07-06
robertzito; Welp;

So far:
1) nvme0n1p2  Is mounted two different ways - only one is permissible!
a) /dev/nvme0n1p2 /  -> as the root system
b) /dev/nvme0n1p2 /var/lib/docker/aufs -> HUH ?/ why ? Presently does not make any sense to me.
c) UUID=9b802392-fb1a-46d2-bb7a-11cb08da2440 /disks/ExtraDrive1 -> sda1 == not a factor

2) sda1 : mounted: /dev/sda1 /disks/ExtraDrive1 ext4 rw,relatime,data=ordered 0 0 ->  no problem found yet .

Mount points are somewhat confusing .

Let's see what we got for  mount points :
```

ls -al /disks/
ls -al /var/lib/docker/aufs

```
see if this turns into a rabbit hole.
Place the outputs Between Code Tags, please, to maintain formatting and readability .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]as a hunt'n we will go
[/INDENT][/INDENT]

---

