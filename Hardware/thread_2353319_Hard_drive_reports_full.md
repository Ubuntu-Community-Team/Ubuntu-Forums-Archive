---
title: "Hard drive reports full"
date: 2017-02-20
forum: Hardware
---

### Post by benzel2 on 2017-02-20
Thanks for taking time to read this, and any advice you can give.  I re-read and edited this several times, I apologize if I'm jumping around a bit.

I've been away from linux for years, and decided to build a server box for Teamspeak, Plex server and rtorrent/rutorrent.

I'm running Ubuntu 16.04 LTS server, installed on a 500 GB SSD, and a 3 GB WD Red mechanical drive.  I built this box at home, and have full access to it. 

I followed a guide to Mount the 3 TB HD as /data and everything appeared to be working fine.  I created a few directories in /data, chown to a user, and set up Plex, rTorrent, and ruTorrent.  I have put less than 500 GB on the mechanical drive, and yet it's full.

I noticed that ruTorrent interface was showing greater than 80% disk usage, and I thought that was just a glitch in the user quota for RuTorrent.  While using WinSCP to transfer files to the /data folder, I noticed the disk usage in ruTorrent kept increasing, and went it reached 100% the file transfer failed, and a warning message popped up in rutorrent.  I started searching the web, and repeatedly, it appears disk quotas are not enabled by default, it's something I would have to install through apt-get.  Great news!  So why is my hard drive full?  Why didn't ubuntu add the 2.7 TB into the available Hard drive space?  Is there a better way to add the second hard drive to my system?  Once I do fill up the 3tb drive, what process should I add a 3rd Hard drive?



I'm not sure what info you need, so here are a few things I read about:

df -ah

```
Filesystem                 Size  Used Avail Use% Mounted onsysfs                         0     0     0    - /sys
proc                          0     0     0    - /proc
udev                       5.7G     0  5.7G   0% /dev
devpts                        0     0     0    - /dev/pts
tmpfs                      1.2G  9.3M  1.2G   1% /run
/dev/mapper/960T--vg-root  208G  198G     0 100% /
securityfs                    0     0     0    - /sys/kernel/security
tmpfs                      5.8G  8.0K  5.8G   1% /dev/shm
tmpfs                      5.0M     0  5.0M   0% /run/lock
tmpfs                      5.8G     0  5.8G   0% /sys/fs/cgroup
cgroup                        0     0     0    - /sys/fs/cgroup/systemd
pstore                        0     0     0    - /sys/fs/pstore
cgroup                        0     0     0    - /sys/fs/cgroup/pids
cgroup                        0     0     0    - /sys/fs/cgroup/net_cls,net_prio
cgroup                        0     0     0    - /sys/fs/cgroup/freezer
cgroup                        0     0     0    - /sys/fs/cgroup/cpu,cpuacct
cgroup                        0     0     0    - /sys/fs/cgroup/memory
cgroup                        0     0     0    - /sys/fs/cgroup/blkio
cgroup                        0     0     0    - /sys/fs/cgroup/cpuset
cgroup                        0     0     0    - /sys/fs/cgroup/devices
cgroup                        0     0     0    - /sys/fs/cgroup/hugetlb
cgroup                        0     0     0    - /sys/fs/cgroup/perf_event
systemd-1                     -     -     -    - /proc/sys/fs/binfmt_misc
hugetlbfs                     0     0     0    - /dev/hugepages
mqueue                        0     0     0    - /dev/mqueue
debugfs                       0     0     0    - /sys/kernel/debug
fusectl                       0     0     0    - /sys/fs/fuse/connections
/dev/sda1                  472M  201M  248M  45% /boot
lxcfs                         0     0     0    - /var/lib/lxcfs
tmpfs                      1.2G     0  1.2G   0% /run/user/1000
tmpfs                      1.2G     0  1.2G   0% /run/user/1002
binfmt_misc                   0     0     0    - /proc/sys/fs/binfmt_misc



```

sudo fdisk -l

```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe6bd5efa


Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 468860927 467859458 223.1G  5 Extended
/dev/sda5       1001472 468860927 467859456 223.1G 8e Linux LVM


Partition 2 does not start on physical sector boundary.




Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 58AD971D-67DB-4FDC-BA50-14673824FB6D


Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 5860532223 5860530176  2.7T Linux filesystem








Disk /dev/mapper/960T--vg-root: 211.3 GiB, 226924429312 bytes, 443211776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/mapper/960T--vg-swap_1: 11.8 GiB, 12616466432 bytes, 24641536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes



```

---

### Post by benzel2 on 2017-02-20
So I was thinking about this some more...perhaps I failed to mount the HDD as /data, and my SDD is really full.  How do I verify and correct this issue?

EDIT**apparently I didn't have an entry in /etc/fstab for the mount, so I created a new mount point called /data2.  it appears I have this correctly now, as /data 2 has 2.6 TB of space now.

```
Filesystem                 Size  Used Avail Use% Mounted onsysfs                         0     0     0    - /sys
proc                          0     0     0    - /proc
udev                       5.7G     0  5.7G   0% /dev
devpts                        0     0     0    - /dev/pts
tmpfs                      1.2G  9.3M  1.2G   1% /run
/dev/mapper/960T--vg-root  208G  188G   11G  95% /
securityfs                    0     0     0    - /sys/kernel/security
tmpfs                      5.8G  8.0K  5.8G   1% /dev/shm
tmpfs                      5.0M     0  5.0M   0% /run/lock
tmpfs                      5.8G     0  5.8G   0% /sys/fs/cgroup
cgroup                        0     0     0    - /sys/fs/cgroup/systemd
pstore                        0     0     0    - /sys/fs/pstore
cgroup                        0     0     0    - /sys/fs/cgroup/pids
cgroup                        0     0     0    - /sys/fs/cgroup/net_cls,net_prio
cgroup                        0     0     0    - /sys/fs/cgroup/freezer
cgroup                        0     0     0    - /sys/fs/cgroup/cpu,cpuacct
cgroup                        0     0     0    - /sys/fs/cgroup/memory
cgroup                        0     0     0    - /sys/fs/cgroup/blkio
cgroup                        0     0     0    - /sys/fs/cgroup/cpuset
cgroup                        0     0     0    - /sys/fs/cgroup/devices
cgroup                        0     0     0    - /sys/fs/cgroup/hugetlb
cgroup                        0     0     0    - /sys/fs/cgroup/perf_event
systemd-1                     -     -     -    - /proc/sys/fs/binfmt_misc
hugetlbfs                     0     0     0    - /dev/hugepages
mqueue                        0     0     0    - /dev/mqueue
debugfs                       0     0     0    - /sys/kernel/debug
fusectl                       0     0     0    - /sys/fs/fuse/connections
/dev/sda1                  472M  201M  248M  45% /boot
lxcfs                         0     0     0    - /var/lib/lxcfs
tmpfs                      1.2G     0  1.2G   0% /run/user/1000
binfmt_misc                   0     0     0    - /proc/sys/fs/binfmt_misc
/dev/sdb1                  2.7T   73M  2.6T   1% /data2
tmpfs                      1.2G     0  1.2G   0% /run/user/1002



```


Does this appear as if I correctly mounted it correctly?  
Question:  since this drive is /media/red  after I mounted it as /data and created a file on it, it doesn't show up when I navigate to /media/red/ ?

---

### Post by ian-weisser on 2017-02-20
Mount the HDD as /tmp (NOT /data)
Move the contents of (SDD) /data to  (HDD) /tmp
Unmount the HDD. Remount the HDD as /data
Edit /etc/fstab to mount the HDD at boot.
Optional: Create a script the runs before starting your torrent client that checks for the properly-mounted HDD at /data.

---

