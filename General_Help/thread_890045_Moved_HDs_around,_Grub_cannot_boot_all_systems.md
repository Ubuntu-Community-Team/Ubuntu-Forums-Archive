---
title: "Moved HDs around, Grub cannot boot all systems"
date: 2008-08-14
forum: General Help
---

### Post by mr_fong on 2008-08-14
I am upgrading my PC and did the following:

- the master HD became slave (hda --> hdb)
- installed a new master HD with Hardy pre-installed (hda2/sdb2)
- the old Edgy system now resides on hdb2 (ex-hda2)

I can boot Hardy from hda2/sdb2 fine. I tried to add an entry to the grub menu so that I can still boot into Edgy, but it will not work.

What I tried in /boot/grub/menu.lst

title		Linux1
root		(hd1,1)
kernel	/vmlinuz root=/dev/hdb2 ro

title		Linux2
root		(hd1,1)
kernel		/vmlinuz root=/dev/sdb2 ro

title		Ubuntu Edgy, kernel 2.6.17-12-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-12-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386

I updated fstab in Edgy to that all Edgy partitions would be mounted as hdb instead of hda. What else did I miss? Linux will boot but it panics and halts. Any help is welcome and much appreciated.

Hans

---

### Post by phidia on 2008-08-14
It would be helpful to know the exact error message you get.
I think you could go into the grub commandline "sudo grub" and at the grub prompt enter "find /boot/grub/stage1". Does that find/output (hd1,1)?
Note that the grub entries you posted are all for the same drive and partition-the sd/hd prefixes don't mean much to the grub commandline.

---

### Post by Too Late on 2008-08-14
Why is your primary master called sdb? I think it should be sda. (Of course, it should be hda, but nowadays every disk is called sd...)

However, to boot into different devices/partitions, you should have different device names mentioned in the 'root' line in the menu.lst file. Now you have only (hd1,1) there. Counting starts from 0, so (hd1,1) means that the OS is to be found from the second partition of the second disk.

edit: By the way, from grub's point of view, the first disk is the disk which is set bootable in BIOS. I don't know, which one is it, since both of them probably have the grub installed and therefore will boot fine. So changing the booting device in BIOS might make the other installation to boot. But you still can't select the starting OS from the menu, because every entry has the same root setting.

---

