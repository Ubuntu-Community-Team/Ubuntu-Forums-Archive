---
title: "Multipath is Default for Identical NVMe Drives"
date: 2021-02-16
forum: Hardware
---

### Post by vincentsaelzler on 2021-02-16
I have four identical NVMe drives.

Ubuntu Server 20.04 recognizes them as multipath devices. They are not multipath devices.

 The [Ubuntu Manpage]("http://manpages.ubuntu.com/manpages/focal/man5/multipath.conf.5.html") indicates they should **not** be configured as multipath devices by default.
>                         _strict_    Both multipath  and  multipathd  treat  only  such  devices  as
                                  multipath  devices  which  have  been  part  of a multipath map
                                  previously, and which are therefore listed in  the  **wwids_file**.
                                  Users  can  manually set up multipath maps using the **multipathd**
                                  **add** **map** command. Once set up manually, the map is remembered in
                                  the wwids file and will be set up automatically in the future.
                        
The default is: [B]strict
[/B]
I suspect that the default value value of [FONT=courier new]find_multipaths[/FONT] is **not** actually [FONT=courier new]strict[/FONT].

**The behavior of the system seems to match the description on the manpage for the _[FONT=courier new]yes[/FONT]_ setting.**
                        > _yes_       Both  multipathd  and  multipath  treat  a  device as multipath
                                  device if the conditions for **strict** are met, [B]or if at least two
                                  non-blacklisted paths with the same WWID have been detected.[/B]

The WWID of the drives is included on [FONT=courier new]/etc/multipath/wwids[/FONT]. When I comment out the WWID and then reboot, another line with the WWID is automatically added to the end.

```
# Multipath wwids, Version : 1.0
# NOTE: This file is automatically maintained by multipath and multipathd.
# You should not need to edit this file in normal circumstances.
#
# Valid WWIDs:
#/eui.00000000010000004ce00018dd8c9084/ #commented out this line, then rebooted.
/eui.00000000010000004ce00018dd8c9084/ #this line was appended automatically.
```

The configuration setting of [FONT=courier new]find_multipaths[/FONT] does not seem to match any of the options described in the manpage. It is "on".
```
sudo multipath -t | grep find_multipaths
    find_multipaths "on"
    find_multipaths_timeout -10
```

Debug output: [FONT=courier new]lsblk
[/FONT]```
$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
...
nvme0n1                   259:0    0   1.9T  0 disk  
&#9500;&#9472;mpatha                  253:1    0   1.9T  0 mpath 
&#9474; &#9492;&#9472;mpatha-part1          253:2    0   1.9T  0 part  
&#9492;&#9472;nvme0n1p1               259:1    0   1.9T  0 part  
nvme1n1                   259:2    0   1.9T  0 disk  
&#9500;&#9472;mpatha                  253:1    0   1.9T  0 mpath 
&#9474; &#9492;&#9472;mpatha-part1          253:2    0   1.9T  0 part  
&#9492;&#9472;nvme1n1p1               259:3    0   1.9T  0 part  
nvme2n1                   259:4    0   1.9T  0 disk  
&#9500;&#9472;mpatha                  253:1    0   1.9T  0 mpath 
&#9474; &#9492;&#9472;mpatha-part1          253:2    0   1.9T  0 part  
&#9492;&#9472;nvme2n1p1               259:5    0   1.9T  0 part  
nvme3n1                   259:6    0   1.9T  0 disk  
&#9500;&#9472;mpatha                  253:1    0   1.9T  0 mpath 
&#9474; &#9492;&#9472;mpatha-part1          253:2    0   1.9T  0 part  
&#9492;&#9472;nvme3n1p1               259:7    0   1.9T  0 part
```

Debug output: [FONT=courier new]udevadm info[/FONT] ([helper script link]("https://unixutils.com/identify-lun-id-wwn-wwid-vendor-name-file-systems-block-device-linux/"))
```
BLOCK_SIZE=1.9T
DEVNAME=/dev/nvme1n1
ID_WWN=eui.00000000010000004ce00018dd8c9084
ID_PATH=pci-0000:09:00.0-nvme-1
--------------
BLOCK_SIZE=1.9T
DEVNAME=/dev/nvme0n1
ID_WWN=eui.00000000010000004ce00018dd8c9084
ID_PATH=pci-0000:08:00.0-nvme-1
--------------
BLOCK_SIZE=1.9T
DEVNAME=/dev/nvme2n1
ID_WWN=eui.00000000010000004ce00018dd8c9084
ID_PATH=pci-0000:0a:00.0-nvme-1
--------------
BLOCK_SIZE=1.9T
DEVNAME=/dev/nvme3n1
ID_WWN=eui.00000000010000004ce00018dd8c9084
ID_PATH=pci-0000:0b:00.0-nvme-1
```


I know that editing the blacklist in [FONT=courier new]/etc/multipath.conf[/FONT] is a successful workaround.

**However, my goal is to determine if this is a bug, and if so, report it to the right people!**

---

### Post by wporr on 2021-11-30
I appear to be having the same issue. Trying to autoinstall with cloud-init. I have an ssd (/dev/sda) and 4 identical nvme's (/dev/nvme*n1). The nvme devices keep getting setup automatically as a multipath device and I'm having trouble removing that feature. Curtin fails because it's trying to use the multipath block device instead of the ssd.

---

