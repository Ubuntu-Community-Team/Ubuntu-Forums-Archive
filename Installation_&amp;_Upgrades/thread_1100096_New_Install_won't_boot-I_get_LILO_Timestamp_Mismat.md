---
title: "New Install won't boot-I get LILO Timestamp Mismatch error"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by joe_kirchner on 2009-03-18
Hi

I am new to Ubuntu and am looking for installation support.

Here is my problem.  I am installing on Ubuntu from the alternate install CD.  It appears Ubuntu did not install the kernel.

Everything went smoothly until I tried to boot up.  At the initial point in booting, I received the "LILO Timestamp Mismatch" error message and the system froze. I tried googling with no luck.  I would prefer Grub, but the Ubuntu install disk did not offer this.

My set up is four drives with four partitions:

1) /boot - Raid 1 - volume group vg_boot/boot
2) /     - Raid 5 - volume group vg_root/root
3) /home - Raid 5 - volume group vg_root/home
4) /srv  - Raid 5 - volume group vg_root/srv
5) /data - Raid 5 - volume group vg_data/data
6) swap  - Swap   - one partition per drive

The machine has 191 Mb RAM

After trying various solutions offered from google search, I reinstalled and got the same error.  Then I checked to see if LILO was pointing to the correct kernel location.  It pointed to a link /vmlinuz, which pointed to boot/vmlinuz-2.6.27-7-generic.  The only problem is that there are no files in the boot directory, not even hidden files.

/boot is mounted.  Here is the output from the mount command:

/dev/mapper/vg_root-root on / type reiserfs (rw,relatime)
/dev/mapper/vg_boot-boot on /boot type ext3 (rw,relatime,errors=continue,data=ordered)
/dev/mapper/vg_data-data on /data type reiserfs (rw,relatime)
/dev/mapper/vg_root-home on /home type reiserfs (rw,relatime)
/dev/mapper/vg_root-srv on /srv type reiserfs (rw,relatime)
tmpfs on /dev type tmpfs(rw)

Do you have any idea where the kernel should be located? Is there any way to get the alternate install CD to install grub instead of LILO?  Is there a quick fix to the LILO Timestamp Mismatch error?  

Thanks,

Joe

---

