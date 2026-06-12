---
title: "Install UNR 9.10 on Asus Eee 2Gb SSD drive"
date: 2010-04-07
forum: Hardware
---

### Post by Vitaly Tch on 2010-04-07
Some days ago i buy netbook Asus Eee PC 2Gb SSD 512 DDR2 for my wife  inet surf.
It comes with winXP home. My wife don't like win systems  and i want to intstall ubuntu.

Standard live CD unr installer  says not enouth space on hard disk, even i try to use all ssd space.

Nice  point will be install liveCD with persistent file directly to  netbook SSD.

This method and work stability not tested. so u can use it on you  own risk :-\"

Ok,  lets go.

I create boot disk on usb stick 16Gb and  placed ubuntu-9.10-netbook-remix-i386.iso there. Use usb-creator from ubuntu only (not unetbootin or some), we need original mbr later.

Boot  from usb stick.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk  /dev/sda: 2000 MB, 2000388096 bytes
255 heads, 63 sectors/track, 243  cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk  identifier: 0x00000000

   Device Boot      Start         End       Blocks   Id  System
/dev/sda1   *           1         243      1951866    b  W95 FAT32

Disk /dev/sdb: 16.2 GB, 16173236224 bytes
64  heads, 32 sectors/track, 15424 cylinders
Units = cylinders of 2048 *  512 = 1048576 bytes
Disk identifier: 0x000c06e3

   Device  Boot      Start         End      Blocks   Id  System
/dev/sdb1    *           1       15424    15794160    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$  
```We see /dev/sda as internal ssd and /dev/sdb as usb  stick

```
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none  on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs  (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sda1  on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none  on /sys/fs/fuse/connections type fusectl (rw)
none on  /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type  securityfs (rw)
none on /dev/pts type devpts  (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs  (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none  on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type  tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs  (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type  binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on  /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon  (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ 
```LiveCD  mount /dev/sda at /cdrom, i think it found vfat mbr. :confused:  Remove it.

```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero  of=/dev/sda bs=446 count=1
1+0 records in
1+0 records out
446  bytes (446 B) copied, 0.00174011 s, 256 kB/s
ubuntu@ubuntu:~$
```/cdrom  marked as ro file system so remount it.

```
ubuntu@ubuntu:~$  sudo mount -o remount rw /cdrom
```Use sudo gparted to create  fat32 partition on /dev/sda and format it.

Reboot system, boot  from stick again.

```
ubuntu@ubuntu:~$ mount
aufs on / type  aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on  /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs  (rw,mode=0755)
/dev/sdc1 on /cdrom type vfat (rw)
/dev/loop0 on  /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type  fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on  /sys/kernel/security type securityfs (rw)
none on /dev/pts type  devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs  (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none  on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type  tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs  (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type  binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on  /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon  (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$
```We see  /dev/sda not auto mounted. Very nice.:grin:

Mount  internal ssd from nautilus. Try usb-creator

```
ubuntu@ubuntu:~$  usb-creator-gtk
```Hmm... internal ssd not in list.:???:

Edit usb-creator code

```
ubuntu@ubuntu:~$  sudo gedit  /usr/share/pyshared/usbcreator/backends/devicekit/backend.py
```in  function def _device_added(self, device) change

```
if not  d.Get(device, 'device-is-system-internal'):
```to 

```
if  d.Get(device, 'device-is-system-internal'):
```ubuntu@ubuntu:~$  usb-creator-gtk

We can see /dev/sda1 in device list now.

Next  step is create live-usb with usb-creator, but it fails with bootloader  install error.](*,)
Ok,  we can try make it without script.

```
ubuntu@ubuntu:~$ sudo  gedit /usr/share/pyshared/usbcreator/install.py
```in  function def install_bootloader(self) comment lines

```
#                 obj.InstallBootloader(self.device,
#                                       dbus_interface='com.ubuntu.USBCreator',
#                                       timeout=MAX_DBUS_TIMEOUT)
``````
ubuntu@ubuntu:~$ sudo  apt-get update
ubuntu@ubuntu:~$ sudo apt-get install mbr
```Make  new mbr

```
ubuntu@ubuntu:~$ sudo install-mbr /dev/sda
```Next  try to use usb-creator

```
ubuntu@ubuntu:~$  usb-creator-gtk
```Use  /cdrom/ubuntu-9.10-netbook-remix-i386.iso

Create max size  persistent file, is about 1.2Gb

All works good, with no errors :)

Some  post installation checks

```
ubuntu@ubuntu:~$ df
Filesystem            1K-blocks      Used Available Use% Mounted on
aufs                     250396     50812    199584  21% /
udev                     250396       252    250144   1% /dev
/dev/sdc1              2017708    1403696    614012  70% /cdrom
/dev/loop0              637824     637824         0 100% /rofs
none                    250396        216    250180   1% /dev/shm
tmpfs                   250396         32    250364   1% /tmp
none                    250396        88     250308   1% /var/run
none                    250396         0     250396   0% /var/lock
none                    250396         0     250396   0% /lib/init/rw
/dev/sda1              1948044    1947244       800 100% /media/6A74-C183
ubuntu@ubuntu:~$
```We  use all space at /dev/sda ssd device.

Shutdown, boot from ssd  hard disk.

Use df command to check how much free space we have at  ssd drive.

Work complete.:biggrin:

Any  suggestions are welcome.


---
Known bugs: Disk utility notification  shows that ssd drive works in non-standart mode. I don't know what it  mean, it don't show more info. When i have some free time will try to  resolve it.

P.S. It's not so good every time see liveCD boot  menu, change language and boot method. If somebody can help to rebuild  liveCD iso file it will be very nice.

P.S.S My english is not  native, I know my post can looks funny:lolflag:

---

