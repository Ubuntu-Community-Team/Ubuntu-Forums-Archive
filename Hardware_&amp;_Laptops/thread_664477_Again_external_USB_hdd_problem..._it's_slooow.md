---
title: "Again external USB hdd problem... it's slooow"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by maxino on 2008-01-11
Hiya,
I just bought an external 80GB USB drive to go together with my ancient IBM Netvista P4 2GHz running happily Xubuntu 7.10. Don't know exact specs, but it's a new one with USB 2.0. 
After creating an ext3 filesystem on it, it was immediately automounted and I got the icon on the desktop. Here are some info:

```
max@max-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00090d5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974        1035      498015   82  Linux swap / Solaris
/dev/sda3            1036        4865    30764475   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6430f2e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
```

```
max@max-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev)
```

It works, but seems to me very slowly: a movie about 1.4GB took about 1h30m to be copied (that should be about 0.26MB/s) and the whole PC was continuously frozen for a few seconds each few minutes or so.
The hdd enclosure has a USB 2.0 interface, not sure about the PC (as I said, it's rather ancient).
I also noticed lots of warnings from the kernel during the copy. Snippet from dmesg output:

```
...
[19013.485387] usb 4-2: reset high speed USB device using ehci_hcd and address 30
[19043.690793] usb 4-2: reset high speed USB device using ehci_hcd and address 30
[19074.319657] usb 4-2: reset high speed USB device using ehci_hcd and address 30
[19137.407057] usb 4-2: reset high speed USB device using ehci_hcd and address 30
[19167.744284] usb 4-2: reset high speed USB device using ehci_hcd and address 30
[19198.141447] usb 4-2: reset high speed USB device using ehci_hcd and address 30
[19228.346852] usb 4-2: reset high speed USB device using ehci_hcd and address 30
...
```

My question is: what kind of speed should I expect from such a setup? Should I worry about those warnings? Any way to speed it up?

Sorry for the length and thanks in advance to everyone.

---

### Post by maxino on 2008-01-15
Sorry for the bump...

Any suggestion?

---

### Post by o.besner on 2008-01-15
Bump... same problem, but with a Western Digital 1TB hard drive in FAT32. 

Drive unmounts randomly, is slower than it normally is, and my computer freeze for a few seconds like described above.

---

### Post by JSP on 2008-01-16
Hello,

I have been bothered with the same issue with a USB2.0 160GB LACIE hard drive. Searching through the various forums I found out that some folks got rid of the "reset high speed USB device using ehci_hcd" message by removing the usb2.0 module:
# rmmod ehci_hcd

But then the kernel uses the usb1.1 which is slower (1.1Mb/s?)

In this post [http://ubuntuforums.org/showthread.php?t=163716](http://ubuntuforums.org/showthread.php?t=163716) , 
Fritztcat suggested to reduce the maximum number of sectors the hdd can read/write at once by doing this:

# echo 128 >/sys/block/sda/device/max_sectors

128 being less than the 240 default.
As it did not do the trick, I have tried with 64, 32, ... 8.
In my case the only results was that the amount of data copied between two resets was reduced - and so did the overall speed.

I finally tried this: 
# echo 1024 >/sys/block/sda/device/max_sectors
The resets did not disappear but this time had a reset on average each 1GByte and I have just a complete DVD at 6Mbytes/s.

I am no specialist - but so far there is an improvement.

---

### Post by maxino on 2008-01-17
Thanks for the tip, I'll try it soon.

Googling around I relized that this very problem appears on almost every distro-dedicated forum (Suse, Fedora, Mandriva, etc) and either the question is left hanging or the workarounds as described above are suggested.

I wonder if it is a confirmed bug of the current USB module...

---

