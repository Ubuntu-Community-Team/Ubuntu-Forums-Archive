---
title: "FastTrak S150 SX4 problems"
date: 2008-10-04
forum: Hardware
---

### Post by Muttonz on 2008-10-04
Hi everyone,
I would like to install Ubuntu on a RAID array with this controller (see subject), but I'm running into a few problems.  First, I don't know that much about Linux. :D  Second, I am getting "No RAID disks" errors.

I am using this Promise PCI card with 3 drives plugged into it.  I also have a separate drive plugged into the motherboard with a SATA cable.  Ubuntu is installed on this separate drive.

I installed dmraid and tried to run it using "sudo dmraid -ay" per the online tutorial, and I get the no RAID disks error.  I then tried a few different commands that the Fake RAID Debug guide suggested, here are the results:

ubuntu@ubuntu:~$ sudo dmraid -ay -vvv -d
NOTICE: creating directory /var/lock/dmraid
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
No RAID disks
WARN: unlocking /var/lock/dmraid/.lock

(I have no idea what that means...)


ubuntu@ubuntu:~$ sudo dmraid -b
/dev/sda:    156301488 total, "6QZ67V9Y"

(Not sure what this number means either...)


ubuntu@ubuntu:~$ sudo dmraid -rD
No RAID disks


ubuntu@ubuntu:~$ sudo fdisk -u -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe5a6e5a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150239879    75119908+  83  Linux
/dev/sda2       150239880   156296384     3028252+   5  Extended
/dev/sda5       150239943   156296384     3028221   82  Linux swap / Solaris


So it looks like SDA is my 80GB drive that is not attached to the RAID array. It doesn't look like the RAID array is showing up at all. :confused:

Promise has a few Linux drivers on their website, but they are for RedHat and Suse, so I didn't know if I could use any of those.  From what I can tell I should be able to setup this fakeRAID software without any drivers and get the RAID working, is this correct?

Any advice and help would be highly appreciated.  Thank you!

- Andrew

---

### Post by Muttonz on 2008-10-16
Sorry to bump, but I'm quite lost.  I don't even know if I'm heading in the right direction by trying to use this fakeRAID utility.

---

### Post by fx260 on 2009-02-14
Hi do you found i Driver.

i can't find a driver form my s150 sx4

Thangs
Tom

---

