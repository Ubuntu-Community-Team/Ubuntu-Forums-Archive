---
title: "CDRom permissions problem ?"
date: 2009-06-25
forum: Hardware
---

### Post by pdc124 on 2009-06-25
i cant get a VM to boot from the CDDROM and k3b doesnt find a drive when I try to burn anything. 


paul@zilly:/media$ sudo lshw -C disk
  *-cdrom
       description: SCSI CD-ROM
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       capabilities: audio
       configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
paul@zilly:/media$

it would appear to be here:

paul@zilly:/media$ dmesg | grep sr
[    2.077002] Driver 'sr' needs updating - please use bus_type methods
[    3.145113] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    3.145493] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.145684] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   18.513317] type=1505 audit(1245913107.842:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1861
[   18.513732] type=1505 audit(1245913107.842:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1861
[   18.847956] type=1505 audit(1245913108.174:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1866
[   18.849104] type=1505 audit(1245913108.178:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1866
[   18.928424] type=1505 audit(1245913108.258:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1870
paul@zilly:/media$

(this is the win2000 installation disk for the VM ) 
paul@zilly:/media/cdrom0$ ls -la
total 640
dr-xr-xr-x 1 root root    666 2002-07-24 13:00 .
drwxr-xr-x 4 root root   4096 2009-06-25 07:58 ..
-r-xr-xr-x 1 root root     45 2002-07-24 13:00 autorun.inf
dr-xr-xr-x 1 root root    336 2002-07-24 13:00 bootdisk
-r-xr-xr-x 1 root root      5 2002-07-24 13:00 cdrom_ip.5
-r-xr-xr-x 1 root root      5 2002-07-24 13:00 cdrom_nt.5
-r-xr-xr-x 1 root root      0 2002-07-24 13:00 cdromsp3.tst
dr-xr-xr-x 1 root root    728 2002-07-24 13:00 discover
dr-xr-xr-x 1 root root 181680 2002-07-24 13:00 i386
-r-xr-xr-x 1 root root  16490 2002-07-24 13:00 read1st.txt
-r-xr-xr-x 1 root root 233472 2002-07-24 13:00 readme.doc
-r-xr-xr-x 1 root root 196880 2002-07-24 13:00 setup.exe
dr-xr-xr-x 1 root root    152 2002-07-24 13:00 setuptxt
-r-xr-xr-x 1 root root  15903 2002-07-24 13:00 spnotes.htm
dr-xr-xr-x 1 root root    192 2002-07-24 13:00 support
dr-xr-xr-x 1 root root    238 2002-07-24 13:00 valueadd


but all the stuff is owned by root 


navigating to /media/cdrom0 in dolphin, as user  is an  empty folder/


So how do i change the permssions on the CDrom at boot ?

---

