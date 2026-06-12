---
title: "Partition lost identity after 9.10 upgrade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by nray on 2009-10-30
I upgraded two systems to 9.10 last night, a desktop and a netbook.  The desktop went smoothly, the netbook did not.

The two things that went differently during the update on the netbook:

1) Started the update earlier, in the middle of the day, updater ran into issues downloading all the files, and it cancelled the update and reverted part way through the download process.
2) Restarted the update later in the day, and at the end of the update process, I chose "Close" and then shut down the system rather than select "Reboot", and booted up the netbook later.

Then, when I tried to boot the netbook to 9.10, I ran into grub problems, said it couldn't find a file (I didn't record the exact error).

Synopsis of problem and solution: The netbook has three partitions, sda1 is an ext2 /boot, sda2 is swap, and sda3 is an ext3 /.  Somehow during the update/shutdown process, the partition for sda1 lost it's identification as an ext2 partition, but was otherwise intact.  The quick solution could have been me booting off a LiveCD, doing a mount -t ext2 /dev/sda1 /mnt, copying all the files somewhere else, mkfs /dev/sda1, copied the files back, umount /mnt, mount /dev/sda3 /mnt, get the new uuid of sda1 with blkid, open up /mnt/etc/fstab and update the uuid then reboot and I'd have been back in business.

(In comparison, my desktop has only two partitions, sda1 swap and sda2 jfs as /, and had no problems after the update.)

What I actually did to try to fix my netbook grub problem was this:

I booted off the LiveCD, tried to mount /dev/sda1 and it refused saying I needed to specify the filesystem type, so I skipped it and mounted sda3, and since it looked complete I forgot about sda1 and it's role and went to work trying to solve the problem (first mistake).

Started a chroot environment on sda3 while booted off the LiveCD, and I installed grub 2.

Grub 2 couldn't find any of my old grub boot info, and couldn't find any linux kernels and refused to add any as a boot option.

I mistakenly thought this had something to do with my chroot environment (second mistake), so I manually edited /boot/grub/grub.cfg (I know, not the right thing to do...)

Rebooted and realized I needed to reinstall the current kernel since it wasn't actually in /boot on sda3

Then I finally realized that my /boot must have been my sda1 partition, which I had trouble mounting in the beginning, and was the real cause of all these problems.

fsck /dev/sda1 found no errors (and didn't complain about the filesystem!)

Checked /etc/fstab on sda3 and verified it was ext2 and did a mount -t ext2 and it mounted fine.

Decided it was going to be just as much work to revert (copy files off sda1, reformat, copy them back, uninstall grub 2, and reinstall grub), so I just reformatted sda1, verified it mounted with no issues, copied the files from /boot on sda3 back to sda1, rebooted, ended up at a "grub rescue>" prompt, went back to the LiveCD, chrooted to my sda3 and sda1 environment, did a "grub-install /dev/sda", then an update-grub2, noticed the "cannot find list of partitions" error, did a sudo blkid -c /dev/null and compared it to /etc/fstab and realized that the uuid of sda1 had changed, and so I updated /etc/fstab and rebooted, and all seems fine now.

I still have no idea how sda1 lost it's identity as ext2, though, and it's somewhat disturbing.  Anyone have any ideas what might have happened?

---

