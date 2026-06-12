---
title: "Ram Not Recognized"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by LongTooth on 2005-06-02
Ubuntu does not seem to recognize all of the ram on my PC. This is a new maching that started out with one stick of 512Mb of PC2700 ram. I recently add a second stick of the same type and brand for a total of 1Gb of ram (2X512). But when I do a 'dmesg' the results do not show Ubuntu utilizing the whole 1Gb of ram. Here are the results:

dmesg
Linux version 2.6.10-5-386 (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri May 20 13:52:48 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000003dff0000 (usable)
 BIOS-e820: 000000003dff0000 - 000000003dff3000 (ACPI NVS)
 BIOS-e820: 000000003dff3000 - 000000003e000000 (ACPI data)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Warning only 896MB will be used.
Use a HIGHMEM enabled kernel.
896MB LOWMEM available.


From the 'dmegs' results I will have to enable the HIGHMEM kernel. But how do I go about doing that? 

Thanks.

---

### Post by kvidell on 2005-06-02
[QUOTE=LongTooth]Ubuntu does not seem to recognize all of the ram on my PC. This is a new maching that started out with one stick of 512Mb of PC2700 ram. I recently add a second stick of the same type and brand for a total of 1Gb of ram (2X512). But when I do a 'dmesg' the results do not show Ubuntu utilizing the whole 1Gb of ram. Here are the results:

dmesg
Linux version 2.6.10-5-386 (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri May 20 13:52:48 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000003dff0000 (usable)
 BIOS-e820: 000000003dff0000 - 000000003dff3000 (ACPI NVS)
 BIOS-e820: 000000003dff3000 - 000000003e000000 (ACPI data)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Warning only 896MB will be used.
Use a HIGHMEM enabled kernel.
896MB LOWMEM available.


From the 'dmegs' results I will have to enable the HIGHMEM kernel. But how do I go about doing that? 

Thanks.[/QUOTE]
 apt-get install linux-686
:) That should do it.
Make sure you clean and preen your /boot/grub/menu.lst
- Kev

---

### Post by LongTooth on 2005-06-02
kvidell, thanks for the quick reply. I'll do that right now. But...clean and preen your /boot/grub/menu.ls...leaves me a little lost. Could you expound? Thanks.

---

### Post by kvidell on 2005-06-02
[QUOTE=LongTooth]kvidell, thanks for the quick reply. I'll do that right now. But...clean and preen your /boot/grub/menu.ls...leaves me a little lost. Could you expound? Thanks.[/QUOTE]
 sudo gedit /boot/grub/menu.lst and clean up all the entries. Remove ones you don't need (as it adds a lot when you add a kernel) and make sure the most current one is first (if it works, so that you don't have to fiddle with the bootloader everytime you boot to get the kernel you want).

---

### Post by LongTooth on 2005-06-02
Looks like this worked! Adding up the numbers I get 991Mbs of ram. But I guess that is as close to 1Gb as one will get. Here are the results of dmesg:

dmesg
Linux version 2.6.10-5-686 (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri May 20 14:31:01 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000003dff0000 (usable)
 BIOS-e820: 000000003dff0000 - 000000003dff3000 (ACPI NVS)
 BIOS-e820: 000000003dff3000 - 000000003e000000 (ACPI data)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
95MB HIGHMEM available.
896MB LOWMEM available.             (for a total of 991MBs)


Anyway, I'm happy. 

As to the /boot/grub/menu.lst. Again here is the output of the menu.lst:


title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

As you can see the two 686 entries are first with two 386s listed afterward. Should I comment out (#) the 386 or delete them all together? And what about the memtest86+? Leave alone or comment/delete?

Thanks.

---

### Post by Klin'Targ on 2005-06-02
[QUOTE=LongTooth]

As you can see the two 686 entries are first with two 386s listed afterward. Should I comment out (#) the 386 or delete them all together? And what about the memtest86+? Leave alone or comment/delete?

Thanks.[/QUOTE]
I think a better solution would be to actually uninstall the 386 kernel (it takes ~60 MB of disk space). To do this, first boot into the 686 kernel, then run ```
sudo apt-get remove linux-386 linux-image-386 linux-restricted-modules-386 linux-image-2.6.10-5-386 linux-restricted-modules-2.6.10-5-386
```
EDIT: Uninstalling the kernel will remove the excess entries from /boot/grub/menu.lst as well.

---

### Post by LongTooth on 2005-06-02
Well, the sudo apt-get remove...did the trick. It also removed the excess entries from /boot/grub/menu.lst as well. I did the remove operation twice. After the first time - and I was informed of the packages deleted - I checked the grub/menu.lst. The listings for the 386 were still there. After the second time - same command - again I was informed of packages removes. This time the grub/menu.lst was corrected and the 386 listing were not there. Thanks to kvidell and Klin'Targ for the help.

---

