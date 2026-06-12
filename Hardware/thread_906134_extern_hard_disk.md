---
title: "extern hard disk"
date: 2008-08-31
forum: Hardware
---

### Post by downloadfreak on 2008-08-31
hello,

I have an extern hard disk 500gb of western digital. It always worked well and there came an icon in my desktop. Now that icon doesn't come and I can't find it anywhere. what can I do?

best regards

---

### Post by eggdeng on 2008-08-31
Plug it in and immediately run ```
dmesg | tail
``` Post the output. Post the output of ```
fdisk -l
``` for good measure.
If you want to try mounting it manually, [see http://ubuntuforums.org/showthread.php?t=405384]("see http://ubuntuforums.org/showthread.php?t=405384")

---

### Post by downloadfreak on 2008-08-31
Where can I do that? sorry but I'm a bit new to ubuntu

---

### Post by eggdeng on 2008-08-31
Applications -> Accessories -> Terminal. Copy and paste the first command, then press Intro. Do the same with the second. You can copy and paste the output from the terminal too.

---

### Post by downloadfreak on 2008-08-31
Ok I opned it and I typed in dmesg I got a really long list for the rest the commands don't seem to react

---

### Post by eggdeng on 2008-08-31
Just copy and paste exactly as follows, first one, then the other. Don't forget to plug in the disk just before you run the first command.
```
dmesg | tail
```
```
fdisk -l
```

---

### Post by downloadfreak on 2008-08-31
Ok I got this now:
rita@rita-laptop:~$ dmesg | tail
[ 7535.405256] usb 2-1.1: USB disconnect, address 7
[ 7536.504600] usb 2-1.2: USB disconnect, address 8
[ 7541.072246] usb 2-1: USB disconnect, address 6
[ 7544.999781] usb 1-2: new low speed USB device using uhci_hcd and address 2
[ 7545.176869] usb 1-2: configuration #1 chosen from 1 choice
[ 7545.198732] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input11
[ 4112.372864] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
[ 4126.723564] usb 2-1: new high speed USB device using ehci_hcd and address 10
[ 7571.785980] usb 2-1: configuration #1 chosen from 1 choice
[ 7590.649655] usb 2-1: USB disconnect, address 10
rita@rita-laptop:~$ fdisk- 1
bash: fdisk-: command not found
rita@rita-laptop:~$ 
rita@rita-laptop:~$

---

### Post by eggdeng on 2008-08-31
My bad. Second command should be ```
sudo fdisk -l
``` In any case, the usb disk doesn't seem to be connecting. Have you been using it on another (W*nd*ws) system? How is it formatted- FAT? NTFS?

---

### Post by downloadfreak on 2008-08-31
> **eggdeng said:**
> My bad. Second command should be ```
sudo fdisk -l
``` In any case, the usb disk doesn't seem to be connecting. Have you been using it on another (W*nd*ws) system? How is it formatted- FAT? NTFS?

Ok I now got to my intern hard disk of 40 gb but I need my extern one of 500 gb

No I haven't been using it on something else than this laptop with ubuntu.

I can't find how it's formated

---

