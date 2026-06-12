---
title: "GRUB problem with new HD Installed"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by ujay on 2005-07-01
I've been running Ubuntu for a while now, with dual boot to an older Mandrake partition.  I added another hard drive, and installed windows 98 on it (simply for playing a couple of games that do not play well with emulators).

To do this without potentially borking the ubuntu install, I physically pulled the power plugs from the existing drives, and installed windows on the new drive.

I have the hard drive mounting in fstab no problem, but cannot get it recognized in GRUB.

I altered /boot/grub/devices.map to the following
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd3)   /dev/hdd  <-- new drive, slaved to cdrom on secondary IDE

I then added the menu option to /boot/grub/menu.lst

# This entry added manually after device install
title         Windows 98
root          (hd3,0)
makeactive
chainloader   +1

When I select the Windows 98 option from the grub bootup menu, I get the message 'Device does not exist'.

I ran the update-grub command, and the same situation still stands.

I've been using linux for several years, but I admit that the grub bootloader is new to me.

df -h shows the following filesystems

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             1.8G  181M  1.5G  11% /
tmpfs                 380M     0  380M   0% /dev/shm
/dev/hda7              66G   19G   44G  31% /home
/dev/hda6             5.5G  1.9G  3.4G  35% /usr
/dev/hdb1             1.9G  257M  1.6G  15% /mnt/hdb.root
/dev/hdb6              21G   17G  3.7G  83% /mnt/hdb.home
/dev/hdb5             5.8G  3.1G  2.4G  57% /mnt/hdb.usr
/dev/hdd1              17G  819M   16G   5% /mnt/win
/dev                  1.8G  181M  1.5G  11% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
/dev/hdc              646M  646M     0 100% /media/cdrom0


and an ls of /mnt/win shows:

autoexec.001  command.com  msdos.---     Program Files  suhdlog.dat
autoexec.bat  config.sys   msdos.sys     recycled       system.1st
bootlog.prv   detlog.txt   My Documents  setuplog.old   win98
bootlog.txt   io.sys       netlog.txt    setuplog.txt   windows


Not sure where to go from here  :-?

---

### Post by ujay on 2005-07-01
Halfway there - I altered the device.map to set /dev/hdd to (hd2).  This time, the system attempted to boot from the device but locked up.  I take it that grub does not play well with the device map having gaps in the sequence.

---

### Post by ujay on 2005-07-01
It looks like I may have to wait for the stable Colony distro.  According to Ubunto.org [http://lists.ubuntu.com/archives/ubuntu-devel/2005-July/008528.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-July/008528.html)

Significant installer changes include:

  * Fixed GRUB configuration when dual-booting with a DOS/Windows
    installation on a hard drive other than the first (#1527).

*** sigh *** :smile:

---

