---
title: "Can not access sda"
date: 2013-04-26
forum: Hardware
---

### Post by dlw on 2013-04-26
Open 'Dash Home',
Click on 'Disk',
Click on '80gb Hard Disk /dev/sda',

The following error appears:
Error mounting /dev/sda1 at /media/dlw/1a9191bd-d5bb-4a8d-b96f-b4eb66a3e4c2: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/dlw/1a9191bd-d5bb-4a8d-b96f-b4eb66a3e4c2"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 (udisks-error-quark, 0)


dlw@dlw-HP:~$ dmesg | tail
[   65.712793] tg3 0000:3f:00.0: eth0: Link is up at 100 Mbps, full duplex
[   65.712799] tg3 0000:3f:00.0: eth0: Flow control is on for TX and on for RX
[   65.713003] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   79.621484] init: ureadahead-other main process (2250) terminated with status 2
[  185.442023] EXT4-fs (sda1): bad geometry: block count 18310546 exceeds size of device (18310400 blocks)
[  207.773806] EXT4-fs (sda1): bad geometry: block count 18310546 exceeds size of device (18310400 blocks)
[  231.038288] EXT4-fs (sda1): bad geometry: block count 18310546 exceeds size of device (18310400 blocks)
[  233.587012] EXT4-fs (sda1): bad geometry: block count 18310546 exceeds size of device (18310400 blocks)
[  233.778605] EXT4-fs (sda1): bad geometry: block count 18310546 exceeds size of device (18310400 blocks)
[  795.359672] EXT4-fs (sda1): bad geometry: block count 18310546 exceeds size of device (18310400 blocks)
dlw@dlw-HP:~$ 

Any help solving this appreciated.
dlw

---

### Post by dlw on 2013-04-26
Solved

---

### Post by dlw on 2013-04-26
Solved

---

