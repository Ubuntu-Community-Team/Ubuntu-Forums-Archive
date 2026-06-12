---
title: "Encrypted root and swap on thumbdrive"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by Arokha on 2009-08-02
Hello! I'm attempting a rather unusual install of Ubuntu, and have run into an issue. I'm trying to make a very multi-purpose thumbdrive, and I'll try to quickly explain that before the issue. Right now the thumbdrive is laid out as...

0: GRUB (legacy, MBR)
-----------
1: NTFS (24gb)
2: ext4 (1gb, /boot, active)
3:extended partition containing...
  4: ext4 (15gb, /, encrypted)
  5: ext4 (15gb)
  6: raw (linux-swap, encrypted)

The eventual goal is to have a working portable Ubuntu, along with GRUB being able to boot some liveCDs from partition 5. The reason for NTFS is because apparently Windows XP can only handle one partition per 'removable media' and always only mounts the first, so it's still a good storage thumbdrive too. 

I can do all that, I believe, but I'm having a problem with encrypted filesystems. I used the 9.04 alternate installer, created my encrypted filesystems, and installed Ubuntu on 4. When I boot to it, GRUB Stage 1 fires off, pushes to 1.5, and 2, and the next thing I see is the Ubuntu splash asking for the password to the drive with a certain UUID, which I have confirmed to be partiton 4. I type in the password, it takes it and says it's right then... nothing. It hangs forever. Without the splash in the way, I can see it is hanging at... "Begin: Waiting for encrypted device... ...". 

Originally, in the initrd, it had /conf/conf.d/cryptroot containing targets for both / and swap, and only / was called by UUID, while swap was called by /dev/sda6 (a bug in the alternate installer's creation of the ramdisk?), which was incorrect on the system I was booting it on. I changed it to be that partition's UUID, and still... nothing. Not sure what to try now! Any help would be appreciated! Please don't just advise against installing it on a thumbdrive... I know it's not the 'best' idea!

Sorry for such a wordy question...

Edit: Also, if I change the UUIDs in cryptroot to be /dev/sdx#, it does ask for both / and swap passwords (yay), but then drops to busybox, saying waiting on root timed out.

Solved: Turns out that you HAVE to use LVM and have the swap and root in the same physical volume, as far as I can tell. I don't know if this is just a bug or my lack of linux knowledge.

---

