---
title: "Mounting RAID at boot"
date: 2010-06-10
forum: Hardware
---

### Post by Mad-One on 2010-06-10
I've just added two 1Tb HDs to my machine as a RAID1 array. My planned setup is my current 500Gb IDE HD for software and the RAID for data. There was nothing traumatic about the RAID set-up; formats and mdadm create went fine. I mounted the RAID and wrote data to it. 

However...when I reboot the RAID is down. I have to restart it and remount it. I know how to mount the array at boot up by adding to the fstab but not how to start the RAID prior to doing this. Can someone enlighten me?

TIA

---

### Post by gsgleason on 2010-06-10
Interesting.  

Upon boot, does this show anything?
```

sudo mdadm --detail --scan

```

Do you have a file /etc/mdadm.conf?  normally the output of the previous command is the content of this file.

What should happen is that your initrd should detect raid arrays automagically.

---

### Post by Mad-One on 2010-06-10
> **gsgleason said:**
> Interesting.  

Upon boot, does this show anything?
```

sudo mdadm --detail --scan

```Do you have a file /etc/mdadm.conf?  normally the output of the previous command is the content of this file.

What should happen is that your initrd should detect raid arrays automagically.

I get: mdadm: md device /dev/md/d0 does not appear to be active.

which I expected as it isn't until I kick it off manuely.

I have .etc/mdadm/mdadm.conf. It reads:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Mon, 07 Jun 2010 21:24:42 +0100
# by mkconf $Id$

```Doesn't look right, does it?

---

### Post by Mad-One on 2010-06-10
OK, decided to RTFM.

I changed the mdadm.conf file to:

```
DEVICE /dev/sdb1 /dev/sdc1
ARRAY /dev/md/0 name=RAID devices=/dev/sdb1,/dev/sdc1
HOMEHOST <system>
MAILADDR root
```I then did an assemble with a scan.

```
sudo mdadm --assemble --scan 
mdadm: no devices found for /dev/md/0
mdadm: /dev/md/0 has been started with 2 drives.
```This started the array which I could then mount.

The question remains "How do I get this start up the array at boot?"

---

### Post by gsgleason on 2010-06-11
If this is caused by the necessary kernel module not being included in the initramfs, you can make sure it gets loaded by adding the module name to /etc/initramfs-tools/modules and then regenerate your initramfs with sudo update-initramfs -u

---

### Post by Mad-One on 2010-06-14
> **gsgleason said:**
> If this is caused by the necessary kernel module not being included in the initramfs, you can make sure it gets loaded by adding the module name to /etc/initramfs-tools/modules and then regenerate your initramfs with sudo update-initramfs -u

I tried this after a complete re-install and no-joy. The machine can see the array; knows it is an array; and what drives make it up but won't start it up. I guess I'll have to make do with a manual start up for the moment.

---

### Post by psusi on 2010-06-14
Adding the entry to mdadm.conf should do it, but you might have to run update-initramfs after.

---

