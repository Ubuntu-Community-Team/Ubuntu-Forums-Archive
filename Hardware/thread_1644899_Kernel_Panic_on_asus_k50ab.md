---
title: "Kernel Panic on asus k50ab"
date: 2010-12-13
forum: Hardware
---

### Post by Chocrates on 2010-12-13
Ubuntu has been locking up a lot since I installed 10.10. I thought it was because of rythmbox but it started doing it simply browsing with firefox.   Finally after it crashed it kernal panic'd and wont load. As far as I know it gets into the initial ram disk and fails when it tries to mount the root fs. I didn't install anything or update un days.   I think this is unfixable and requires a format, but my disk drive doesn't quite work......   does anybody have an idea as to how to fix this? Or have hears of this crashing problem?

---

### Post by drs305 on 2010-12-13
> I think this is unfixable and requires a format, but my disk drive doesn't quite work.

Hard drive or CD-drive? 

You might be able to update/restore your initrd image.

If you can boot a LiveCD, use the Step 1 chroot procedure from the following link up to and including the 'sudo chroot /mnt/temp' command.
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

At that point, you should be at the root prompt and in your real Ubuntu installation. Try recreating the initrd image with the following. Since you are in a chroot environment, you don't need to use "sudo".

The first command should display the current initrd images. Use the latest version in the second command (-generic may or not be attached to the image you use):
```
ls /mnt/temp/boot/initrd.img*
update-initramfs -u -v -k 2.6.XX-xx-xxxxxx
```

Example: update-initramfs -u -v -k 2.6.35-23-generic

---

### Post by Chocrates on 2010-12-13
> **drs305 said:**
> Hard drive or CD-drive?


Cd drive.
Ill give it a try if I can get it to load the cd. Ill see about getting a bootable usb stick if not

Edit:

Victory! Thanks

I didn't think the initial ram disk was ever overwritten so how could it have gotten corrupted?

---

