---
title: "Hard drive seems to have died"
date: 2008-09-23
forum: Hardware
---

### Post by zaxor0 on 2008-09-23
This post is so i can attach a file to help with the "investigation" of what happened to my drive, which is going on in the irc.

---

### Post by IntuitiveNipple on 2008-09-23
For those that are interested in what this thread is about. Zack reported a lost disk issue (corrupted master boot record) in the #ubuntu forum on IRC. After he posted the sector here we were able to see it was a Windows boot sector, which came from when he used Windows to install onto a second disk.

Using the LiveCD on the PC, we then set up a [remote SSH link using a shared screen session](http://tjworld.net/wiki/Howto/MultiuserScreenWithSshForSupervisedRemoteSupport) so I could connect to the PC and his terminal and he could see what I was doing.

We found that only sector 0 had been over-written... sector 1 onwards had GrUB's stage 1.5 files.

We then used testdisk to analyse the disk. It found the back-up MBR and wrote it back to the drive on our instruction.

Then we used losetup to connect the device to a loop device to check it, and then the linux file-system in partition #1 on another loop device which was then mounted so Zack could save valuable documents.
```

sudo losetup /dev/loop1 /dev/sda
sudo losetup -o32256 /dev/loop2 /dev/sda
sudo mkdir -p /mnt/linux
sudo mount /dev/loop2 /mnt/linux

```

With the files saved the PC was rebooted so the kernel could detect the new partition table and we tried re-installing the grub boot sector:
```

sudo mkdir -p /mnt/linux
sudo mount /dev/sda1 /mnt/linux
sudo mount -o bind /proc /mnt/linux/proc
sudo mount -o bind /dev /mnt/linux/dev

sudo chroot /mnt/linux

grub

grub> find /boot/grub/stage2

grub> setup (hd0) (hd0,0)

grub> quit

exit

sudo umount /mnt/linux/dev
sudo umount /mnt/linux/proc
sudo umount /dev/sda1
sync

```
When the system was restarted it booted successfully.

---

