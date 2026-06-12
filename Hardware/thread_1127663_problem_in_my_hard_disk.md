---
title: "problem in my hard disk"
date: 2009-04-16
forum: Hardware
---

### Post by Gladiator-prog4me on 2009-04-16
hello 

ubuntu 9.04 

i have a problem in my hard disk  

when i try to open the partitions or mount it 

i got this error : 

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

i have restart my computer , and i still got the error  

please help me 

thank you

---

### Post by taurus on 2009-04-16
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Gladiator-prog4me on 2009-04-16
> **taurus said:**
> What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

thank you my friend 

this the output  

root@Mohamed-Desktop:/home/mohamed# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001eb68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         985     7911981   82  Linux swap / Solaris
/dev/sda2   *         986        5471    36033795   83  Linux
/dev/sda3            5472       19457   112342545   83  Linux
root@Mohamed-Desktop:/home/mohamed# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=57d6717e-34ad-432d-9d9b-698754ae142c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=e3325931-9cb6-4147-b2ba-f6d924f0d5a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
root@Mohamed-Desktop:/home/mohamed# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              34G   11G   22G  32% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  112K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  140K  1.8G   1% /dev
tmpfs                 1.8G  164K  1.8G   1% /dev/shm
lrm                   1.8G  2.4M  1.8G   1% /lib/modules/2.6.28-11-generic/volatile
root@Mohamed-Desktop:/home/mohamed#

---

### Post by taurus on 2009-04-16
Are you talking about /dev/sda3 or another harddrive?

---

### Post by Gladiator-prog4me on 2009-04-16
> **taurus said:**
> Are you talking about /dev/sda3 or another harddrive?

no  

the partition i was talking about , it was not appear

---

### Post by taurus on 2009-04-16
```
dmesg | tail
```

---

### Post by Gladiator-prog4me on 2009-04-16
> **taurus said:**
> ```
dmesg | tail
```

root@Mohamed-Desktop:/home/mohamed# dmesg | tail
[   30.273144] vboxdrv: Successfully loaded version 2.2.0 (interface 0x000a0009).
[   31.875910] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.875914] Bluetooth: BNEP filters: protocol multicast
[   31.892794] Bridge firewalling registered
[   37.271805] sky2 eth0: enabling interface
[   37.271970] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.390885] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   39.391084] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   49.448016] eth0: no IPv6 routers present
[  103.634948] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

---

### Post by taurus on 2009-04-16
Unplug the drive.  Then plug it back in.  Now, run that command again?  What brand and model of your external drive anyway?

---

### Post by Gladiator-prog4me on 2009-04-16
> **taurus said:**
> Unplug the drive.  Then plug it back in.  Now, run that command again?  What brand and model of your external drive anyway?

i have do that , and this the result  

mohamed@Mohamed-Desktop:~$ dmesg | tail
[   30.102387] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   30.102390] vboxdrv: Successfully loaded version 2.2.0 (interface 0x000a0009).
[   31.671719] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.671724] Bluetooth: BNEP filters: protocol multicast
[   31.687857] Bridge firewalling registered
[   37.264184] sky2 eth0: enabling interface
[   37.264361] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.300889] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   39.301027] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   49.644025] eth0: no IPv6 routers present

---

### Post by taurus on 2009-04-16
I assume it is an external drive?  Have you tried to see if you can read/access that drive with another computer, running windows perhaps?

---

### Post by Gladiator-prog4me on 2009-04-17
> **taurus said:**
> I assume it is an external drive?  Have you tried to see if you can read/access that drive with another computer, running windows perhaps?


now , i have a try to open this partition from another computer ( ubuntu 8.10 ) and it working fine ! 

so the problem in ubuntu 9.04 

can you help me to fix this ?

---

### Post by sharon.gmc on 2009-04-17
format your hard drive.

---

### Post by Gladiator-prog4me on 2009-04-17
> **sharon.gmc said:**
> format your hard drive.

i can't sir , because i have a important data ! 

can you help me to fix this problem but don't format ?

---

### Post by taurus on 2009-04-17
Wait for the jaunty final release or connect that harddrive back to the machine that has intrepid running since it can access that harddrive, according to you.

---

### Post by Gladiator-prog4me on 2009-04-17
> **taurus said:**
> Wait for the jaunty final release or connect that harddrive back to the machine that has intrepid running since it can access that harddrive, according to you.

thank you my friend 

now i have reinstall the ubuntu 9.04 

and my computer and hard drive working fine  

thank you alot

---

