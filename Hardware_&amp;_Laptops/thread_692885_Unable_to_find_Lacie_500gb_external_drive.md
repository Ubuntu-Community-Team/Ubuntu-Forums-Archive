---
title: "Unable to find Lacie 500gb external drive"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by Dalstal on 2008-02-10
I have a new Lacie 500gb external drive but I'm having some major problems making my computer detect and mount it, what shuld I do?
My linux knowledge is unfortunately much to limited to solve the problem without help.
I've owned and managed to use an identical drive before but I don't get this one to work.

/Mattias

---

### Post by PmDematagoda on 2008-02-10
Post the outputs of:-
```
sudo fdisk -l
```
and
```
cat /etc/mtab
```
when you plug the external hard disk into your PC.

---

### Post by Dalstal on 2008-02-10
dalis@Dalis:~$ sudo fdisk -l
[sudo] password for dalis:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d3a0d39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

dalis@Dalis:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
dalis@Dalis:~$

---

### Post by PmDematagoda on 2008-02-10
Were the commands executed after the external USB drive was plugged in?

If so, post the output of:-
```
lsusb
```

---

### Post by Dalstal on 2008-02-10
Yes the drive was plugged into the usb (and still is)

dalis@Dalis:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
dalis@Dalis:~$

---

### Post by PmDematagoda on 2008-02-10
That does not look good, did you check your external drive on a different PC or OS to see if it works?

---

### Post by Dalstal on 2008-02-11
I tried it a few minutes ago on a different computer with win XP without any success, looks like this one is going back to the store:/

---

