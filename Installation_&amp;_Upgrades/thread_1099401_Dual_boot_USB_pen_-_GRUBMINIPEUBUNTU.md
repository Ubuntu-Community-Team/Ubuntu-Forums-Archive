---
title: "Dual boot USB pen - GRUB/MINIPE/UBUNTU"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by msjones on 2009-03-18
Hi,

Long time since I have posted on here. I am having issues with a project.

I have a 2GB USB pen drive. I have it in 3 partitions. I have the grub boot loader installed along with mini pe. I also have the ubunut live image extracted to the 3rd partition. Grub works fine, so does booting to minipe, my issues is with booting ubuntu live from partition 3.

Heres what I have done:

```
mount -o loop ubuntu-8.10-i38.iso /mnt/iso
mount /dev/sdc3 /mnt/usb
cp -a /mnt/iso/* /mnt/usb/
umount /mnt/usb
umount /mnt/iso
```

So as you can see I have mounted the ISO and extracted it to partition 3.

My problem is I cant get it to boot from grub. As I have said before minipe boots from grub fine. What grub command do I need to run the live files from this pen?

Thanks in advance for any help!

---

### Post by dandnsmith on 2009-03-18
I haven't tried that one (yet), having been concentrating on getting a usb stick to multi-boot distros using syslinux.

You might get some mileage out of using vmlinuz and initrd.gz as the kernel and initial ramdisk from the casper directory in the copy you've made.
I just don't know what error messages would then pop up to indicate further problems to be solved.

---

### Post by rtom on 2009-03-18
If you already have GRUB on the pendrive, did you try to adjust the /boot/grub/menu.lst file?

---

### Post by msjones on 2009-03-18
> **rtom said:**
> If you already have GRUB on the pendrive, did you try to adjust the /boot/grub/menu.lst file?

Thats where I am stuck, I just need the command to get the image to boot from grub.

---

### Post by rtom on 2009-03-18
In order to locate the vmlinuz (and initrd) files, you can use the ```
find vmlinuz
``` command. This will display the partitions which contain a vmlinuz file. Then 
```
root	 (hd0,4)
``` sets the 4. partition as root device, you need to adjust it to yours
```
kernel	 /boot/vmlinuz-2.6.17-10-generic
``` load appropiate kernel
```
initrd	 /boot/initrd.img-2.6.17-10-generic
``` load appropriate initrd
```
boot 
```

This is usually applied on HDDs, but hope works on pendrives as well.

---

### Post by keith2045 on 2009-06-08
> **msjones said:**
> Hi,

Long time since I have posted on here. I am having issues with a project.

I have a 2GB USB pen drive. I have it in 3 partitions. I have the grub boot loader installed along with mini pe. I also have the ubunut live image extracted to the 3rd partition. Grub works fine, so does booting to minipe, my issues is with booting ubuntu live from partition 3.


I know this is an old thread but i have been trying to get grub with minipe and a few other linux distros on a usb pen drive for a while. I can boot into linux and can boot into minipe on a few select systems. Can you post how you got grub to work with minipe? On a few systems grub doesnt want to boot minipe

Thanks

---

