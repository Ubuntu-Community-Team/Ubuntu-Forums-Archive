---
title: "New External HDD hangs IPL"
date: 2009-11-24
forum: Hardware
---

### Post by bedachtm on 2009-11-24
I have been using a 500GB USB drive formatted in NTFS for backup for a long time now. It sits on top of my machine and is never turned off individually. I never had any problems - I put the drive in fstab and it always mounted and was shared with my local network (another Ubuntu netbook and an XP desktop.) Recently I ran out of space, so I got a 1.5 TB to replace it.

I just formatted the new drive, as EXT3, and all was well - started using it right away.

The problem occurred the first time I tried to IPL with the new drive attached and turned on (like with the old one). The whole system hangs with a black screen and a blinking cursor point in the top left. Powering down the drive, then restarting the system again resolves the problem. Once running the drive can be switched on and it mounts and is usable!

Can anybody tell me what is wrong? I really would like to be able to turn this drive on a forget about it.

---

### Post by Zteam on 2009-11-24
If I were you I would try to test the drive with the manufacters harddrive diagnostic tool, I'm not sure but maybe Ultimate BootCD contains something useful even for external devices, otherwise you can try the disk with another computer, check the cables etc...

---

