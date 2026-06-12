---
title: "Raid stopped mounting at boot"
date: 2015-09-22
forum: Hardware
---

### Post by mobious2 on 2015-09-22
Hello,

I am very new to Ubuntu and I am having a bit of a problem with my Raid 5 array no longer mounting at boot. I am getting the error > "[COLOR=#111111][FONT=Consolas]The disk drive for /data is not ready yet or not present
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]Continue to wait; or Press S to skip mounting or M for manual recovery"[/FONT][/COLOR]. After logging in, fdisk -l doesnt show the array but after running modprobe rr64x, I can mount the array and everything works. 

I am currently using Ubuntu 14.04 and the raid 5 array is built on a RocketRaid 640 card with 4 Seagate 2tb drives. To install the Rocketraid card I used the instructions found at [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid) and then patched the drivers with the patch found at [https://help.ubuntu.com/community/RocketRaid?action=AttachFile&do=view&target=rocketraid-linux-3.11-patch-r2.tar.bz2](https://help.ubuntu.com/community/RocketRaid?action=AttachFile&do=view&target=rocketraid-linux-3.11-patch-r2.tar.bz2). Initially, after patching I was able to mount the array partition and then format and everything worked fine for a few days. Last night, while after I moved all of my media to the array and was tinkering in Plex the server restarted and since then I get the above error. I am not sure how to pull any logs.

If it helps, I followed the instructions for > [SIZE=1][COLOR=#333333][FONT=Ubuntu]Updated and simplified procedure for Ubuntu 13.04 or later[/FONT][/COLOR][/SIZE] to install the RocketRaid card.

Here is my /etc/fstab, the drive not mounting is /dev/sdb1

> /dev/mapper/nostromo--vg-root /               ext4    errors=remount-ro 0       1# /boot was on /dev/sda1 during installation
UUID=0e295abf-7f05-4250-9365-bd73d3ebb240 /boot           ext2    defaults        0       2
/dev/mapper/nostromo--vg-swap_1 none            swap    sw              0       0
/dev/sdb1       /data       ext3    defaults        0       0




---

### Post by mobious2 on 2015-09-23
I tried changing the fstab to mount the array based on the UUID.. Still no luck...Just taking a shot in the dark.. Since it mounts after I run modprobe rr64x.. Could it be a driver issue or a dkms issue? Any idea how I would check that?

---

