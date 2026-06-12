---
title: "A installation problem"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Gusgus on 2009-05-06
Hello everyone:

I installed Ubuntu 8 on my usb memory and it runs well
but now I have a problem, everytime I tried to boot
my computer without the usb memory, it show this error:

GRUB Loading Stage1.5

Error 21

Now I can only used windows vista if the usb memory
is on the laptop, otherwise I just get stuck on this error
and it doesn't let choose vista OS.

I hope someone can help me on this.

Thanks in advance.

---

### Post by Brandon Williams on 2009-05-07
It sounds like you installed grub to the master boot record of your laptop. You may have to figure out how to restore the original MBR in order to boot windows without the USB. Another option is to install mbr to your MBR, which should cause it to boot from the first bootable partition on the hard drive.

First, though, a question ... When you boot from the USB stick, do you have to do anything to make your machine boot from USB? Does the laptop appear to be using only the USB, or does it think that it's booting from the HDD?

If it appears to be booting from the HDD, try this: boot into ubuntu and run 'sudo install-grub */dev/sdb*', where */dev/sdb* is the device designation for the USB stick. After this, reboot and modify your bios config to ensure that it is booting from the USB with no reference to the HDD. Then, complete booting the rest of the way into ubuntu. You should not do anything to the MBR on your HDD until you have verified that you can boot into both windows and ubuntu using the MBR on your USB stick. _After_ you have verified this, you can consider ways to remedy your original issue.

---

### Post by Gusgus on 2009-05-07
When I boot the laptop with the USB connected, it show me a menu with the OS installed (Ubuntu, Windows) by default it selects ubuntu but I can choose windows if I want to with no problem. 

If I don't have the usb connected, then it show me error 21. 

I restarted the computer and I tried to choose a different boot device, so I pressed ESC and it shows me a menu with 2 boot devices options: DVD and notebook HardDrive. I choose the HD but it still sent me the error 21.

It seems like it's looking the grub (I don't know what's that) in the hard-drive and when it doesn't find it, it shows me the error.

I have to say that I have never used linux, I don't have any expirience with it.

---

### Post by Gusgus on 2009-05-10
Anyone?

---

### Post by dstew on 2009-05-10
As mentioned before, when you installed Ubuntu onto your USB stick, the installer put the grub boot loader stage 1 onto your hard disk Master Boot Record (MBR). Grub stage 2, which shows the menu and loads the operating system, is on your USB stick. So, you cannot boot your computer without your USB stick plugged in.

If you want to boot the computer without the USB stick plugged in, you will need to put grub stage 2 onto the hard disk, and re-install the boot loader so it will pick up its stage 2 from there. Otherwise, you should re-install the Windows boot loader using the Windows Recovery Console, fixmbr command.

If you want an independent bootable system on the USB drive, you need to re-install grub to the MBR of the USB stick. Then, you need to change your system BIOS to boot the USB stick before it tries to boot the hard disk. Not all BIOSes can boot USB sticks, and not all USB sticks can be booted. If the only options on your BIOS boot menu are the hard disk and the DVD drive, you might be out of luck.

---

