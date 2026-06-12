---
title: "Disk order and partitions get screwed up on adding new hardware!"
date: 2008-05-13
forum: Hardware
---

### Post by Keldek on 2008-05-13
Ok, I'm a bit at wits end here, but I'll try to remain as calm and collect as I can...

I was having serious trouble getting my (onboard) promise FastTrack T3 SAS raid controller drivers to compile and install... so I went to the next best thing, or so I thought...

Disabled the onboard raid controller in my bios, and installed a Silicon Image SIL3114 SATA Host Controller PCI card...

fire the comp back, everything runs properly, Ubuntu boots just fine.

Upon running 'sudo fdisk -l' I'm showed that the 2 new drives on the raid controller have become /dev/sda and /dev/sdb

My initial disk setup looked like this:

/dev/sda -- 250GB boot drive, 5 partitions /boot, /, /var, /home, and swap
/dev/sdb -- 250GB NTFS disk holding my stored files until I get my other disks conferted
/dev/sdc -- 250GB Empty disk, no partition table at this time
/dev/sdd -- 256MB usb flash drive

When I reboot, my disk order is now as follows:

/dev/sda -- 300GB disk 1 on raid card <-- Device ID = linux raid auto
/dev/sdb -- 300GB disk 2 on raid card <-- Device ID = linux raid auto
/dev/sdc -- 250GB boot drive
/dev/sdd -- 250GB NTFS disk
/dev/sde -- 250GB empty disk <-- device ID = Linux
/dev/sdf -- 256MB usb flash drive

So I thought, ok no problem... I'll just use the new layout, create my raid array in mdadm, and update my /etc/fstab and /etc/crypttab accordingly.

WRONG!

I create the needed partitions on /dev/sda and /dev/sdb according to the info fdisk gave me, I am correct.

Didn't notice that /dev/sdb couldn't resync because it was busy...

'mdadm --create /dev/md0 --chunk=16 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1'

mdadm could create the array because /dev/sdb was busy (I forget the actual message)

go back into fdisk and make sure I did everything properly, yep.. 'w' to write and exit on /dev/sdb...

I forget the exact error but it went something like this:
syncing disks
could not create new partition tables on /dev/sdb: drive device locked or busy
will use new tables on next reboot

Now, this seems a bit strange considering /dev/sdb is not being used...

I don't think much of it, recheck /etc/fstab and /etc/crypttab and reboot

And here's where the fun begins
screen stops at "loading hardware files" something or another, and my hdd LED and usb flash LED go berserk.

So I let it sit, nothing.

And now I'm sitting here with a half broken system using the live cd because I don't know where I went wrong...

and now, fdisk tells me something COMPLETELY different!

/dev/sda -- 250GB boot disk
/dev/sdb -- 250GB NTFS disk
/dev/sdc -- 250GB empty disk <-- Device ID = Linux raid auto
/dev/sdd -- 300GB disk 1 on raid card <-- Device ID = linux raid auto
/dev/sde -- 300GB disk 2 on raid card <-- Device ID = Linux
/dev/sdf -- 256MB usb flash drive

Now, This actually seems like the peoper layout to me, why it listed something completely different when I booted into my normal ubuntu is beyond me, but I'm kind of lost on what to do next as I'm a bit worried that if I make partition table changes on the live CD something will get seriously screwed up when I try to reboot to the live system.

What really bothers me is that somehow my empty 250 gb disk went from Linux to Linux RAID auto and my 300GB disk went from Linux Raid Auto to Linux. Which is my main reason for not wanting to proceed in making any more changes.

And to make things worse, I can't open my luks drive to check (for the 4th time) my /etc/fstab and /etc/crypttab files
```
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda3 /dev/mapper/sda3_crypt
Enter LUKS passphrase: 
Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /dev/sda3 contains at least 258 sectors.
Failed to read from key storage
Command failed: No key available with this passphrase.

ubuntu@ubuntu:~$ 

```

I don't know that I'm making much sense here, but I hope that I am and I hope someone out there can help.

---

