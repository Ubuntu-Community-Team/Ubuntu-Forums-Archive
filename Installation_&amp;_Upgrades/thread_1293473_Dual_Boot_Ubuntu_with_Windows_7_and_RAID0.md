---
title: "Dual Boot Ubuntu with Windows 7 and RAID0"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by rplanet on 2009-10-17
Hello,
i'm new, my name is Marko and this is my first post.

First thing first, here there is my config:

Asus P6T V2
Intel Core i7 720
6GB DDR-3 RAM
2HD 640GB in RAID0 Striped via ICH10R controller
nVidia Geforce GTX 260 892MB
Windows 7 Ultimate 64bit

I would like to install ubuntu in dual boot with my Windows 7 but I won't lose RAID for my Windows installation.

Now, how can I install Ubuntu in dual boot with Windows 7?

If I'll add a third hard disk and I'll install Ubuntu on this third hard disk and then I'll boot the Ubuntu installation with F8 for select the hard disk that I want to boot from, could be a solution?

Thank You so Much.

---

### Post by tosk on 2009-10-17
You'll need a third drive. The linux kernel doesn't support RAID with the Intel ICH10R chipset. So Ubuntu will see both your RAID drives as two AHCI drives, instead of a single drive (the array) which will destroy your RAID setup.

---

### Post by stolp on 2009-10-17
Hi Guys,
I got a
Asus PT6 i7
2 SSD in RAID0 (striped) With win 7 on it.

whut i want is:
a third drive 160 gig
part. 1 100 gig ntfs (data storage)
part. 2 56  gig ext4 (ubuntu linux)
part. 3  x  gig swap (linux swap)

The problem is:
My win 7 keeps starting up not giving me grub menu.
I think it has to do where you put the bootloader...am i right?
If so where the hell should i put it.

And about he array youre right indeed it dous give you two sepperate disks and the combined raid disk. i dont dare touch it but if i can write to it the boatloader id guess id goes in te.
Combined raid drive on the smal partition win 7 makes... but thats a guess and i don't dare destroy my array on the ssd's.

Hope to get some advice...

---

### Post by tosk on 2009-10-17
GRUB was probably installed to the MBR on your third drive. What you'll have to do to switch between them is use the BIOS boot selector to choose what to boot. Most BIOSes have F11 or F12 as the hotkey during initialization. When you press it, it brings up a menu of drives you can boot from.

When it comes up, you can use it select to boot from your RAID array for Windows 7 or to boot your third drive for Linux.

---

