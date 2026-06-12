---
title: "Xubuntu won't boot. -bash: /dev/null: Permission denied"
date: 2008-09-09
forum: General Help
---

### Post by s_s_sparky on 2008-09-09
Here's the background. I was trying to unmount my thumb drive and it just wouldn't unmount. An empty window would pop up and nothing would happen.  I exited the blank window and it said "unable to unmount" my thumb drive. So I restart my laptop with drive still attached.

When it tries to reboot it goes through the normal process but then asks for login and password.  I type that in and then get "-bash: /dev/null: Permission denied" Then I can't do anything and xubuntu doesn't boot.  

Any ideas? :confused:


This may help.  Right before it gives the login it shows this:

[ 15.032000] hda:dma_intr: status=0x51 {DriveReady SeekComplete Error }
[ 15.032000] hda:dma_intr: status=0x40 (UncorrectableError }, LBAsect=4981210, sector=4981207
[ 15.032000] ide: failed opcode was: unknown
[ 15.032000] end_request: I/O error, dev hda, sector 4981207
[ 15.032000] EXT3-fs error (device hda1): ext3_get_inode_loc: unable to read inode block - inode=312259, block=622643
.: 195: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
inti: rcS main process (2343) terminated with status 2
.: 195: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
inti: rc2 main process (2353) terminated with status 2

Ubuntu 7.10 (none) tty1

(none) login:

*Edit*

After I log in I get "-bash: /dev/null: Permission denied" over and over again until I Ctrl+C.

---

### Post by s_s_sparky on 2008-09-11
Bump?

---

### Post by john.nicholls on 2008-09-11
Have you tried searching for that error message on Google?

---

### Post by s_s_sparky on 2008-09-12
Yes and I haven't found anything.  Found a couple forums but there was never any solution.

---

### Post by phalanxjc on 2008-09-13
check out this bug and see if their solution works

[https://launchpad.net/ubuntu/+bug/63031](https://launchpad.net/ubuntu/+bug/63031)

---

### Post by niteshifter on 2008-09-13
Hi,

> [ 15.032000] hda:dma_intr: status=0x51 {DriveReady SeekComplete Error }
[ 15.032000] hda:dma_intr: status=0x40 (UncorrectableError }, LBAsect=4981210, sector=4981207
[ 15.032000] ide: failed opcode was: unknown
[ 15.032000] end_request: I/O error, dev hda, sector 4981207
[ 15.032000] EXT3-fs error (device hda1): ext3_get_inode_loc: unable to read inode block - inode=312259, block=622643

Hate to be the bearer of bad news, but your hard drive is dying. This part:

> error: '/etc/init.d/rc' exited outside the expected code flow.
inti: rcS main process (2343) terminated with status 2
.: 195: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
inti: rc2 main process (2353) terminated with status 2

explains the /dev/null error message: bash goes nuts if the system is not init'd properly. Some of the init.d scripts are corrupted.

Semi-good-news: It might not be the drive itself, it could be a cabling / connector issue. But the damage to files has already been done. Recover from backups or reinstall.

---

