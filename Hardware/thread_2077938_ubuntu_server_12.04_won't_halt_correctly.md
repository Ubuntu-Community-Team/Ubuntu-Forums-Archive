---
title: "ubuntu server 12.04 won't halt correctly"
date: 2012-10-29
forum: Hardware
---

### Post by effyeah on 2012-10-29
When I try to halt the system with "sudo halt" or "sudo shutdown now", I get this at the end of the shutdown process, and the computer doesn't actually shut off: 

```
*Stopping MD monitoring service mdadm --monitor
*Asking all remaining processes to terminate...
*All processes ended within 3 seconds....
*Deconfiguring network interfaces...
*Deactivating Swap...
umount2: Device or resource busy
umount: /var/lib/ureadahead/debugfs busy - remounted read-only
*unmounting local filesystems...
mount: / is busy
* will now halt
[5899.178687] System halted.
```

Except it doesn't actually halt! I have to manually restart it! That's not such a big deal, except when the system reboots, it TAKES FOREVER! It sits and fsck's /dev/sdl1 EVERY SINGLE TIME I BOOT, even with "sudo shutdown -r now" or "sudo reboot".

```
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sdl1: clean, 279856/9814016 files, 2853733/39226112 blocks
```

I don't know what this means exactly or how to prevent it. I had some issues with booting for a while due to something I did while troubleshooting a boot issue I had when the last motherboard I had (older) couldn't remember its boot order in BIOS when more than 12 SATA drives were present. (There's a 20tb raid5 in this machine, but sdl1 is the boot drive, not in the raid array):

```
user@media-PC:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid5 sdk1[0] sdi1[2] sdj1[1] sdh1[3] sdg1[5] sdf1[6] sdb1[11] sda1[10] sdc1[9] sde1[7] sdd1[8]
      19533829120 blocks super 1.2 level 5, 512k chunk, algorithm 2 [11/11] [UUUUUUUUUUU]

unused devices: <none>

```

I don't remember what I did to try to fix the booting issue, but I eventually replaced the motherboard, and it has done this before and after the motherboard swap. I do remember possibly putting a different version of mount or automount or something on, then maybe removing it?

Any idea what the heck could be causing this? I can provide any logs or information necessary, just tell me what info is relevent!

---

