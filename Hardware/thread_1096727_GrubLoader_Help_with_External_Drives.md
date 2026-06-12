---
title: "Grub/Loader Help with External Drives"
date: 2009-03-15
forum: Hardware
---

### Post by invisible39 on 2009-03-15
Ok, this might sound similar to loads of other people's stuff but I'd like to run it past you guys anyway.

I installed Ubuntu onto my external drive, and after some playing around got everything to boot ok. When the external drive is off, it boots to Windows and when it's on it comes up with a loader that allows me to select the OS. 

This works great.

The thing is, to get that to work the boot order has to boot the USB External drive first, which is ok - except when I have my second drive plugged in. 

If the second drive is plugged in, and the Linux drive is off - no OS is found.

So, is there any way to get around this?

Thank you.

---

### Post by meierfra. on 2009-03-15
I suggest to write zeros to the first 440 Bytes of your second usb drive:

```

sudo dd if=/dev/sdX of=sdX.backup bs=1 count=440
sudo dd if=/dev/zero of=/dev/sdX bs=1 count=440
```

Here sdX needs to be replaced by the device name of the second usb drive., its should be  sdb or  sdc. (Use "sudo fdisk -lu" to determine the device name)

The first line is just to backup  the first 440 bytes. It might come in handy if you accidentally apply the commands to the wrong drive. 

Be very careful with the "dd" commands. If applied incorrectly it can wipe a whole hard drive.  If the "dd" command runs for more than just a couple of seconds, stop the process with "Ctrl+C".

---

### Post by invisible39 on 2009-03-16
That sounds scary as hell... haha, I'll give it a go.

Would this affect any data on the drive, or does it move so that the first 440 are empty?

---

### Post by meierfra. on 2009-03-16
> That sounds scary as hell... haha 
Sorry for making it sound so scary. Most people don't include any warning when they recommend that command. I'm just trying to be extra cautious.


> Would this affect any data on the drive, or does it move so that the first 440 are empty? 

It does not move any data. It plainly erases the first 440 bytes of the second USB drive. This first 440 bytes contain some code which is used for booting from that drive. But since don't want to boot from the drive,  you don' t need that code. I hope, if you erase that code, your bios will bypass the external drive and boot from the internal drive. 

Your partition starts much later. So no  actual Data is erased.

---

