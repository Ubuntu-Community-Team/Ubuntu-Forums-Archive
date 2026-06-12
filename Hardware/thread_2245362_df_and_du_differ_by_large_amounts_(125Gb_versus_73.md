---
title: "df and du differ by large amounts (125Gb versus 73Gb) - Unable to determine why"
date: 2014-09-23
forum: Hardware
---

### Post by victorhooi on 2014-09-23
Hi,

We have a HP DL380 G5 server running Ubuntu Server 14.04.1 (LTS), with a BTRFS root file system:

The root drive appears to be filling up, and I can't seem to work out why.

Output of df:
```

$ df -h
Filesystem         Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p1  135G  125G  9.3G  94% /
none               4.0K     0  4.0K   0% /sys/fs/cgroup
udev               990M  4.0K  990M   1% /dev
tmpfs              200M  1.9M  199M   1% /run
none               5.0M     0  5.0M   0% /run/lock
none              1000M     0 1000M   0% /run/shm
none               100M     0  100M   0% /run/user
/dev/cciss/c0d0p1  135G  125G  9.3G  94% /home

```

Output of /proc/partitions:
```

$ cat /proc/partitions
major minor  #blocks  name

 104        0  143305920 cciss/c0d0
 104        1  141209600 cciss/c0d0p1
 104        2          1 cciss/c0d0p2
 104        5    2094080 cciss/c0d0p5

```

Output of mount:
```

$ mount
/dev/cciss/c0d0p1 on / type btrfs (rw,relatime,subvol=@)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu)
cgroup on /sys/fs/cgroup/cpuacct type cgroup (rw,relatime,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,relatime,hugetlb)
/dev/cciss/c0d0p1 on /home type btrfs (rw,relatime,subvol=@home)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)

```

Output of du -chs on /:
```

$ sudo du -chs *
9.7M	bin
174M	boot
4.0K	dev
8.3M	etc
5.4G	home
4.0K	initrd.img
4.0K	initrd.img.old
1.2G	lib
4.0K	lib64
0	media
0	mnt
0	opt
du: cannot access ‘proc/14648/task/14648/fd/4’: No such file or directory
du: cannot access ‘proc/14648/task/14648/fdinfo/4’: No such file or directory
du: cannot access ‘proc/14648/fd/4’: No such file or directory
du: cannot access ‘proc/14648/fdinfo/4’: No such file or directory
0	proc
8.0K	root
1.9M	run
13M	sbin
36G	srv
0	sys
4.0K	system.properties
48K	tmp
1.5G	usr
28G	var
4.0K	vmlinuz
4.0K	vmlinuz.old
73G	total

```

lsof doesn't seem to return any deleted files:
```

$ lsof | grep deleted

```

Also, I've done a server reboot, and the available space did not change.

Any thoughts on what else I can check?

Regards,
Victor

---

### Post by sotiris2 on 2014-09-23
What is the output of [code]sudo btrfs fi df /[code] show?

---

### Post by victorhooi on 2014-09-24
Hi,

Output of "sudo btrfs fi df /":

```

$ sudo btrfs fi df /
[sudo] password for victorhooi:
Data, single: total=132.64GiB, used=122.88GiB
System, DUP: total=8.00MiB, used=20.00KiB
System, single: total=4.00MiB, used=0.00
Metadata, DUP: total=1.00GiB, used=700.39MiB
Metadata, single: total=8.00MiB, used=0.00

```

That's strange, so is it saying that 122Gb is actually used up?

Is the "du" that returns 73Gb used missing something?

Regards,
Victor

---

### Post by sotiris2 on 2014-09-24
I 'm afraid I can't give you a straight answer here. Searching the web yields a lot of results that show du and df will usually show different results but I am not so sure it's to the scale shown here. Brtfs also apparently has some issues with reporting free space as well as having a big overhead. Still not so sure these can justify this huge difference.

Did you always use a different volume for /home?

---

### Post by victorhooi on 2014-10-11
Hi,

@sotiris2: As far as I know, the partition layout hasn't been changed since we ran the Ubuntu Server installer. Below is the output of lsblk:
```

$ lsblk
NAME           MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
cciss!c0d0     104:0    0 136.7G  0 disk
&#9500;&#9472;cciss!c0d0p1 104:1    0 134.7G  0 part
&#9500;&#9472;cciss!c0d0p2 104:2    0     1K  0 part
&#9492;&#9472;cciss!c0d0p5 104:5    0     2G  0 part

```

And my /etc/fstab:
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/cciss/c0d0p1 during installation
UUID=d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7 /               btrfs   relatime,subvol=@ 0       1
# /home was on /dev/cciss/c0d0p1 during installation
UUID=d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7 /home           btrfs   relatime,subvol=@home 0       2
# swap was on /dev/cciss/c0d0p5 during installation
UUID=119e00c3-6b4f-49aa-b5b0-4736d5398c28 none            swap    sw              0       0

```

I'm not sure what's happening here - both "/" and "/home" are pointing to the same drive - but it's some BTRFS sub-volume, right?

The available space definitely seems to be going down - I just checked again with df:
```

$ df -h
Filesystem         Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p1  135G  128G  6.5G  96% /
none               4.0K     0  4.0K   0% /sys/fs/cgroup
udev               3.0G  4.0K  3.0G   1% /dev
tmpfs              597M  1.4M  596M   1% /run
none               5.0M     0  5.0M   0% /run/lock
none               3.0G     0  3.0G   0% /run/shm
none               100M     0  100M   0% /run/user
/dev/cciss/c0d0p1  135G  128G  6.5G  96% /home

```

The amount of free space is getting perilously low, and I'm not entirely sure where it's all going...

Cheers,
Victor

---

### Post by victorhooi on 2014-10-11
Hi,

Well, mystery solved. I thought I'd check to see if there was snapshots, just in case. I hadn't actually ever used the BTRFS snapshot feature myself, but it seems that somehow apt had?

```

victorhooi@ensign-primary:~$ sudo btrfs subvolume list /
ID 256 gen 538192 top level 5 path @
ID 258 gen 538183 top level 5 path @home
ID 300 gen 133385 top level 5 path @apt-snapshot-release-upgrade-saucy-2014-03-08_18:49:36
ID 321 gen 197496 top level 5 path @apt-snapshot-release-upgrade-trusty-2014-05-24_21:47:44

```

Anyhow, I'm not too familiar with the BTRFS syntax for deleting snapshots, and apparently actually removing the apt snapshots is quite a convoluted process:

[http://blog.lyte.id.au/2013/03/08/deleting-an-apt-snapshot-btrfs-subvolume-is-hard/](http://blog.lyte.id.au/2013/03/08/deleting-an-apt-snapshot-btrfs-subvolume-is-hard/)

However, I installed apt-btrfs-snapshot, and did it using that:

```

victorhooi@ensign-primary:~$ sudo aptitude install apt-btrfs-snapshot
The following NEW packages will be installed:
  apt-btrfs-snapshot
0 packages upgraded, 1 newly installed, 0 to remove and 24 not to upgrade.
Need to get 7,272 B of archives. After unpacking 93.2 kB will be used.
Get: 1 http://mirror.internode.on.net/pub/ubuntu/ubuntu/ trusty/universe apt-btrfs-snapshot all 0.3.4.2 [7,272 B]
Fetched 7,272 B in 0s (18.5 kB/s)
Selecting previously unselected package apt-btrfs-snapshot.
(Reading database ... 198376 files and directories currently installed.)
Preparing to unpack .../apt-btrfs-snapshot_0.3.4.2_all.deb ...
Unpacking apt-btrfs-snapshot (0.3.4.2) ...
Setting up apt-btrfs-snapshot (0.3.4.2) ...

```
```

victorhooi@ensign-primary:~$ sudo apt-btrfs-snapshot list
Available snapshots:
@apt-snapshot-release-upgrade-saucy-2014-03-08_18:49:36
@apt-snapshot-release-upgrade-trusty-2014-05-24_21:47:44

```
```

victorhooi@ensign-primary:~$ sudo apt-btrfs-snapshot delete @apt-snapshot-release-upgrade-saucy-2014-03-08_18:49:36
Delete subvolume '/tmp/apt-btrfs-snapshot-mp-6yh7d4kd/@apt-snapshot-release-upgrade-saucy-2014-03-08_18:49:36'

```
```

victorhooi@ensign-primary:~$ sudo btrfs fi df /
Data, single: total=132.64GiB, used=126.17GiB
System, DUP: total=8.00MiB, used=20.00KiB
System, single: total=4.00MiB, used=0.00
Metadata, DUP: total=1.00GiB, used=747.30MiB
Metadata, single: total=8.00MiB, used=0.00

```
```

victorhooi@ensign-primary:~$ sudo apt-btrfs-snapshot delete @apt-snapshot-release-upgrade-trusty-2014-05-24_21:47:44
Delete subvolume '/tmp/apt-btrfs-snapshot-mp-z6mesd36/@apt-snapshot-release-upgrade-trusty-2014-05-24_21:47:44'

```

When I checked the space right afterwards, it hadn't changed:
```

victorhooi@ensign-primary:~$ sudo btrfs fi df /
Data, single: total=132.64GiB, used=124.66GiB
System, DUP: total=8.00MiB, used=20.00KiB
System, single: total=4.00MiB, used=0.00
Metadata, DUP: total=1.00GiB, used=634.98MiB
Metadata, single: total=8.00MiB, used=0.00

```

However, when I waited a few minutes:
```

victorhooi@ensign-primary:~$ sudo btrfs fi df /
Data, single: total=132.64GiB, used=80.31GiB
System, DUP: total=8.00MiB, used=20.00KiB
System, single: total=4.00MiB, used=0.00
Metadata, DUP: total=1.00GiB, used=446.02MiB
Metadata, single: total=8.00MiB, used=0.00
victorhooi@ensign-primary:~$ df -h
Filesystem         Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p1  135G   82G   53G  61% /
none               4.0K     0  4.0K   0% /sys/fs/cgroup
udev               3.0G  4.0K  3.0G   1% /dev
tmpfs              597M  1.4M  596M   1% /run
none               5.0M     0  5.0M   0% /run/lock
none               3.0G     0  3.0G   0% /run/shm
none               100M     0  100M   0% /run/user
/dev/cciss/c0d0p1  135G   82G   53G  61% /home

```

It's a shame this wasn't made clearer, but anyhow at least we're not going to run out of space...haha.

Regards,
Victor

---

