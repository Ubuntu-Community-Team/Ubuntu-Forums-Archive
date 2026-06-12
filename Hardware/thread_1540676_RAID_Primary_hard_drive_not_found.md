---
title: "RAID: Primary hard drive not found"
date: 2010-07-28
forum: Hardware
---

### Post by chrille112 on 2010-07-28
I have installed RAID 1 with mdadm and it seems to work looking att /proc/mdstat

I wanted to test the system, so I removed the power cable for one of the disks. When I startup I get this message:

Primary hard drive 0 not found

And cannot start. I'm not sure if there is something in BIOS or in the RAID config? Any ideas?

---

### Post by jacekk015 on 2010-07-28
Where you have installed OS.
On this RAID1 array ??

Did he finish syncing ??

---

### Post by chrille112 on 2010-07-28
Yes on both questions :)

---

### Post by paulisdead on 2010-07-28
First make sure that the bios is set to roll over to the second drive if the first is not found, this varies a bit from bios to bios.  There might be options to control the hard disk boot order in addition to other devices.

I know the software RAID setups I've done at install time, do not write grub out to the second hard disk on their own.  I think it was just "sudo grub-install /deb/sdb" or whatever your second hard disk was.  I'd double check that command, since I'm less familiar with grub2.

---

### Post by chrille112 on 2010-07-28
It doesn't matter wich hard drive I'm turning off, none of them works alone.

I have looked in the BIOS but can't find anything about rolling over. Both primary hard drives are set to "auto", I suppose that is the roll over you are referring to.

It's an old Dell machine I'm playing with if that helps?

I have installed both disks on the same IDE cable, and set the jumper on the drives to Cable Select. Is that right?

fdisk -l says "/dev/md0 doesn't contain a valid partion table", could that be the problem? How do I solve that?

---

### Post by jacekk015 on 2010-07-28
> **chrille112 said:**
> Yes on both questions :)

There is a setting for mdadm, that prevents from loading OS on degraded array.
```
If you choose to place the root partition on a RAID array, the installer will then ask if you would like to boot in           a *degraded* state.  See [the section called “Degraded RAID”]("https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html#raid-degraded") for further details.             
```Please run this and check it. I assume that you are using latest 10.04 version?

[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html#raid-degraded](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html#raid-degraded)

```
sudo dpkg-reconfigure mdadm
```

---

