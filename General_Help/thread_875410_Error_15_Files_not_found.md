---
title: "Error 15: Files not found"
date: 2008-07-30
forum: General Help
---

### Post by Joots on 2008-07-30
My set up is 2 hd with Windows XP installed on first hd and Ubuntu on second hd. I get error 15: file not found when booting from grub. I can only boot to Ubuntu when I go to the bios boot menu and select the second hd. I would like to be able to select which OS I can boot into from grub boot menu. Any help is very much appreciated.
here's a copy of my menu.lst

default 1

timeout 10

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d31b27f1-b7ea-4dd9-8c79-73f22f12af7e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d31b27f1-b7ea-4dd9-8c79-73f22f12af7e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by fooman on 2008-07-30
please run the following in a terminal and post the output back here:

```
sudo fdisk -l
```

---

### Post by Dieseler on 2008-07-30
I used the instructions from this thread and it works great.

[http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

I have Ubuntu drive as master and Windows drive as slave both drives set to cable select.
Bios set to same except Cd rom is first boot, then The Ubuntu. Don't think it matters after that cause grub will give you the option.
Not sure it would work with the Windows disk set to master.
I don't think it would.
I feel you're pain by the way.

---

### Post by paul382 on 2008-08-21
This means that grub cannot read your (hd0,2) partition.  Is it ext3?
Have you copied the 'ext3fs_stage1_5 (or similar) into your
/boot/grub?.

Check the location of your LFS kernel and enter the correct path. If still problem persist then recover your missing file using [Linux recovery]("http://www.data-recovery-linux.com") software and boot system again.

---

