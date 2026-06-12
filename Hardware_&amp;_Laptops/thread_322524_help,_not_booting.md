---
title: "help, not booting"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by big z on 2006-12-20
help to day i come to boot up my pc and i get the error message: ramdisk : ran out of compressed data

invalid compressed format(err-1)
kernel panic -not syncing: VFS: unable to mount root fs on unknow-block(o,o)

im using 6.10 i368

---

### Post by tkjacobsen on 2006-12-20
Have you compiled your own kernel? 'Cause it sounds like you don't have a ramdiskimage (initrd)

Also try to check your /boot/grub/menu.lst for a line like this

initrd /boot/vmlinuz-2.6.15-26 (the same version as the kernel image (vmlinuz))

If you are not sure post your menu.lst here

---

### Post by big z on 2006-12-20
no i did not compile my own kernal

---

### Post by Sef on 2006-12-21
> Also try to check your /boot/grub/menu.lst for a line like this

initrd /boot/vmlinuz-2.6.15-26 (the same version as the kernel image (vmlinuz))

If you are not sure post your menu.lst here

Could you give some instructions on how to get the menu.lst, please.   Thank you.

---

### Post by big z on 2006-12-21
um yeah how do you get to menu.lzt would it  be easyer to just reintsall

---

### Post by big z on 2006-12-21
bump

---

### Post by tkjacobsen on 2006-12-22
you can get to menu.lst with the following command

gksudo gedit /boot/grub/menu.lst

---

### Post by big z on 2006-12-22
thanks but no thanks cuse after the error message it freezes.

---

