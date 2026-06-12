---
title: "can a usb port damage an external device?"
date: 2010-09-21
forum: Hardware
---

### Post by Andrew Golightly on 2010-09-21
hi all,

We have 3 computers at our place. My external harddisk recently died - the computer still registers that something was plugged in, but I can no longer access the contents.

We also recently bought a device that plugs into a USB port on a computer. After chatting with technical support, we believe it to be faulty, as none of the computers seem to even register that an external device was plugged in. Although lights on it come on showing that it is being powered.

A thought that crossed my mind, was can a USB port (from an old laptop) cause damage to external devices? We have tried other things like USB keys, printers.. and they work fine..

thanks :guitar:

---

### Post by CharlesA on 2010-09-21
It's unlikely that a usb port by itself will cause damange to an external device. If a usb port senses a surge or short, it'll "turn off" and just not work.

It sounds like the external drive just gave up the ghost.

Does anything show up if you so this:

```
sudo fdisk -l
```

---

### Post by pricetech on 2010-09-21
Not impossible, but the likelihood is minute.  You probably just have a dead drive.

---

### Post by Andrew Golightly on 2010-09-21
Yeah, I think it is just dead. My output from sudo fdisk -l is


> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008101f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59372   476903424   83  Linux
/dev/sda2           59372       60802    11481089    5  Extended
/dev/sda5           59372       60802    11481088   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System

So it seems to recognise it's been plugged in (the 320 Gb external drive), but it's not showing up in any other way.. namely the files!

thanks for the feedback around USB ports. We'll keep on plugging in external devices into that other older laptop then.

---

### Post by CharlesA on 2010-09-21
It looks like it sees it, but doesn't see any partitions on it. See if you can see any partitions on it with gparted.

---

### Post by Andrew Golightly on 2010-09-21
Nope. no partitions.

I guess I could try and partition it again?
I'm aware I'll lose all the data on it, but at least maybe I could use it again yeah?

---

### Post by CharlesA on 2010-09-22
Try test disk first to see if you can recovery any partitions that were on there before.

---

### Post by Andrew Golightly on 2010-09-23
Well... miracles do happen.

I decided to add a partition anyway, and format it as the data on it was elsewhere too. It worked. It gave some error about a mountpoint, so I took it to Windows 7 and ran a thorough disk check on it. All passed. Then took it back to Ubuntu and ran a smart check/scan of it. All healthy apparently.

Watched a movie from it last night. So I'm stoked it's all going again, just a little curious as to how it suddenly lost it's partition??? hence the question that started this thread.

thanks again guys for your ideas. You've helped save my external disk from recycle land.

A

---

### Post by Andrew Golightly on 2010-09-23
Well... miracles do happen.

I decided to add a partition anyway, and format it as the data on it was elsewhere too. It worked. It gave some error about a mountpoint, so I took it to Windows 7 and ran a thorough disk check on it. All passed. Then took it back to Ubuntu and ran a smart check/scan of it. All healthy apparently.

Watched a movie from it last night. So I'm stoked it's all going again, just a little curious as to how it suddenly lost it's partition??? hence the question that started this thread.

thanks again guys for your ideas. You've helped save my external disk from recycle land.

A

---

