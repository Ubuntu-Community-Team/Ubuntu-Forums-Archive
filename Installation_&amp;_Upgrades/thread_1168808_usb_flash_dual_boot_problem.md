---
title: "usb flash dual boot problem"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by jolivelli on 2009-05-24
Hello,

I wanted to try a full install of Ubuntu, but I didn't want to re-partition my hard drive, so I installed 9.04 from CD onto a 4GB USB Flash drive. I wanted to have the PC boot to ubuntu if I had the USB drive plugged in, and Vista if I didn't. I thought that if I installed it to the USB drive, it wouldn't make any changes to my internal hard drive. I guess I should have read more before I tried the Install, because that is not what I wound up with. After finishing the install, my PC wouldn't boot at all. I had the bios set to boot from USB first, then CD, the HDD. if I plugged in the USB drive, it would just freeze after the bios screen. if I didn't the installer placed GRUB on my hard drive, and it would give me error 21, and freeze. Fortunately I was able to fix things somewhat by changing the boot order in my bios to boot to the hard drive first. Now, if the USB flash drive is plugged in, GRUB boots ub, and gives me a choice of Ubuntu or Vista. I can boot into either, and use either. My problem is that if I don't have the USB flash drive plugged in, the PC will not boot at all. I would like to have my computer boot to vista if the usb drive is not plugged in. Ideally, I would like to have the USB drive bootable if it is plugged in, and set to boot first from the bios, but this is secondary, my main concern is being able to boot my computer without the USB drive.  Any help would be much appreciated.

Thanks
- Jean Paul

---

### Post by jolivelli on 2009-05-25
Bump :)  Can anyone help me??

---

### Post by ronparent on 2009-05-27
It appears that if the usb flash is not plugged in, that you are trying to boot to a grub menu that is no longer there! Therfore you have written the grub bootloader to the mbr of the hard drive set to boot first (or maybe the usb hard drive). It's hard to tell from your description if you have a separate usb hard drive plugged in when you are trying all of this. 

For your purpose: 1) it would be best that grub boot from the mbr of the usb flash. 2) That the next boot drive in sucession if the usb flash is not plugged in have the bootloader for vista in the mbr. This should also be the drive that vista is installed on. 

To accomplish the 1st objective above, boot from the live cd with the usb stick in and run the following series of commands in a terminal (the cd has to be 1st boot device in bios):

[B]sudo grub
grub> find /boot/grub/stage1
grub> root (hdx,y)
setup (hdx)
grub> quit[/B]

In this series of commands the output of the **find**... will be (hdx,y) - substitue the numbers given for the **root**... command. Same for **setup**...You may have to **sudo gedit /boot/grub/menu.lst** To find the right boot drive for vista. 

With the bios set to boot the vista drive 1st if there is no usb stick or cd and the mbr on that drive restored for vista, the system should now boot to vista. If the usb stick is in, the grub boot menu should prest you with the alternative of either. 
If you are still having problems finding windows at this point post the output of the **sudo fdisk -l** command here and someone can help you. Good luck.

---

