---
title: "ntldr is missing &amp; unable to boot into winxp...in a dual os.."
date: 2008-09-28
forum: General Help
---

### Post by uarpit on 2008-09-28
hi...i had xp before and then i installed debian as a dual boot....i think by mistake i deleted some impotant file..now iam getting an error "NTLDR MISSING"...and iam not able to fix it, as my system is nither booting into xp cd nor detecting it....and in my bios settings 1st booting device is cdrom...my debian is working fine, but iam not able to use xp...

iam fairly new to debian..linux for that matter...so if anyone could help me out with this please...any suggestion is welcomed...thank u...

---

### Post by Jeroensum on 2008-09-28
Can you please paste the output from:

sudo fdisk -l

and

cat /boot/grub/menu.lst

---

### Post by taladan on 2008-09-28
There's a couple of ways that you can fix this, but what you're going to need is an XP cd.  You'll have to drop the cd in the tray, explore it and go to I386 directory, copy the ntldr file from that directory either onto a thumb drive or onto your desktop, then mount the ntfs partition and copy the file over with something like:

```
sudo mount -t ntfs /dev/<partition> /mnt
cd /mnt/WINDOWS
cp ~/Desktop/ntldr .
cd ~
sudo umount /mnt

```

where <partition> is the partition that your windows is located on, ferex: sda1

You should then be able to boot into your windows partition.  The mount command may give you some trouble about wanting to mount the windows partition but it should give you instructions on how to mount it correctly if it barfs an error.

Hope this helps,
Tal

---

