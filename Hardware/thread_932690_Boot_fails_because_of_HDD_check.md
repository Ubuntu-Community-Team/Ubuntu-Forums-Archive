---
title: "Boot fails because of HDD check"
date: 2008-09-28
forum: Hardware
---

### Post by hammedhaaret on 2008-09-28
Hello

I dualboot ubuntu and XP. Works great.
Last week windows crashed and I had to pull the plug to reboot.
Ever since, ubuntu starts a harddisk check on boot and fails whereafter I get send to a root terminal.
I can press 'esc', skip it and boot flawlessly with ubuntu working, as far as I know.
wierd thing is that the check is on sda2 which is my linux partition.

Anyone got an idea what to do?

specs:
Intel C2D 1.8 GHz
Nvidia 7600

---

### Post by mindoms on 2008-09-28
fsck stops and puts you there if it encounters an error that can't be fixed without loss of data. Some files could be lost.

I Usually just run
```
sudo fsck /dev/sda2
```
if some files are lost, they are printed on screen.
keep in mind that you should unmount the disk before:
```
sudo umount /dev/sda2 
```

if /dev/sda2 is the disk, where ubuntu is installed, then you should boot from a live cd (ie the ubuntu install cd) and run it from there.

if you have more then one harddisk installed, check if /dev/sda2 is still the right one:
```
sudo fdisk -l /dev/sda
```

hth, stefan

---

