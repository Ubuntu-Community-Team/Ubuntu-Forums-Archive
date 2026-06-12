---
title: "Unable to eject DVD drive (tray)"
date: 2010-12-17
forum: Hardware
---

### Post by sridharpandu on 2010-12-17
I run Ubuntu 10.10 (MM) on an Acer 5745. I am unable to eject the tray on my DVD drive by navigating to Places|Computer|CD/DVD Drive. (I don't have an eject buttin on the drive). This is strange considering that I installed MM from a DVD. I am not able to figure out whats wrong. Any help would be appreciated.

My /etc/fstab contents are given bekow

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/Monsoon-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c94aa79c-9ccf-45c9-b0e8-fde15b7544c5 /boot           ext2    defaults        0       2
/dev/mapper/Monsoon-swap_1 none            swap    sw              0       0

---

