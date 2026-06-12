---
title: "serious problem"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by windowsatemyhomework on 2005-09-11
I have lost access to my Windows XP entirely. I had been having problems with the OS selection menu that appears when I booted up - the Windows XP option wasn't working, it was giving me the following error:```
     Booting 'Microsoft Windows XP Professional'

root     (hd1,0)
     Filesystem type unknown, partition type 0x7
savedefault
chainloader +1
```So I was having to change the boot order of the drives to switch between Windows and Ubuntu. I tried to fix this by reinstalling Ubuntu, putting the GRUB bootloader onto (hd1,0), the partition of my other drive that had Windows on it.

Now if I boot from the drive with Windows on it, I get the choice of which OS to load, but neither works. Like before, if I boot from the drive with Ubuntu on it, I get the same error message when trying to get into Windows, but Ubuntu works.

So I can't get into Windows AT ALL unless I can

a) fix the error message I was getting before so that I can load either OS when I get the menu from the Ubuntu drive

OR

b) Get the GRUB bootloader off of my Windows drive so that I can switch between the two by changing the boot order like before.

I really need to get back into Windows, so any help is appreciated.

---

### Post by mlomker on 2005-09-12
If you make the Windows hard drive the first disk and then boot to your WinXP cd you should be able to go into the recovery console.  From there the **fdisk /mbr** command would restore the Windows boot loader to the drive.

---

