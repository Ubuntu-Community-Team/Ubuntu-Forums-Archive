---
title: "Prroblems running an NTFS external hard drive..."
date: 2009-03-31
forum: Hardware
---

### Post by Astinos53 on 2009-03-31
I've just switched to Ubuntu (8.10), from Windows XP and I'm having trouble reading my HDD. It worked perfectly fine on Windows but now it doesn't. I get the following:

$LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is  marked to be in use.

Suggestions?

---

### Post by lindsay7 on 2009-03-31
This is most likely not going to be your best answer, but, I had the same problem and it just went away by itself. I looked at old posts and internet searches and did find a lot about usb drives having something to do with it. I had been moving usb drives around and also booting from windows a lot at the time.  Anyway, after a few Ubuntu boots, I could see and use my whole windows partition. I can not explain it, I am just happy I can.

---

### Post by thefirstone on 2009-04-01
I've had the same problem. I have dual boot WindowXP and Ubuntu. It seems that if I exit WindowsXP without unmounting the external hdd when I boot into Ubuntu the drive wont mount in Ubuntu. I need to boot back into WindowsXP and properly disconnect the external drive and when I boot into Ubuntu again the external drive mounts just fine. I don't know why or how but if the drive isn't properly disconnected Ubuntu sees it as still in use.
Hope this was helpful.

---

### Post by kanikilu on 2009-04-01
> **Astinos53 said:**
> I've just switched to Ubuntu (8.10), from Windows XP and I'm having trouble reading my HDD. It worked perfectly fine on Windows but now it doesn't. I get the following:

$LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is  marked to be in use.

Suggestions? Either take the suggestion in the previous post and safely remove the drive from Windows, or, you can force it to mount, by doing the following. These commands need to be run in a terminal, so go to Applications > Accessories > Terminal.

Create mountpoint:```
sudo mkdir /media/usbdrive
```
Mount the drive:```
sudo mount -t ntfs-3g /dev/sdb1 /media/usbdrive -o force
```
You should now be able to browse to it in the file browser (nautilus) or in the terminal. When you are done, just be sure to unmount it before removing it:```
sudo umount /media/usbdrive
```

---

### Post by Astinos53 on 2009-04-01
Okay, so I can access it now. I've decided I'm going to format it again with Ubuntu so I can use it freely without having to manually mount it every time.. I've moved the files on there to my laptop, so how do I go about formatting it?

Thanks for the help!

---

### Post by kanikilu on 2009-04-01
> **Astinos53 said:**
> Okay, so I can access it now. I've decided I'm going to format it again with Ubuntu so I can use it freely without having to manually mount it every time.. I've moved the files on there to my laptop, so how do I go about formatting it?

Thanks for the help! The easiest way to format it is with gparted, which should be in System > Administration > Partition Editor, or run **gksu gparted** from the command line. Just make sure the drive is not mounted, but still plugged in, as you can't format a mounted partition.

---

