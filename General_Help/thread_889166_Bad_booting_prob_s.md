---
title: "Bad booting prob :s"
date: 2008-08-13
forum: General Help
---

### Post by ...alex on 2008-08-13
Ok, heres the deal.

I had a windows installation, then i used Ubootin(i think it was called) to install the newest Ubuntu. It all seemed to go ok, then i was at the final "you need to restart your system" and i did so.

When i booted, straight after the mobo splash screen i got:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

Because it is a laptop and it has no CD ROM, FDD or anything i have used the network to install Windows etc...

I thought it would be clever of me to use the same network boot disk setup (Barts) that i used for windows to go into fdisk and delete the non-dos (linux) partition. All this did was change it from Error 17 to Error 18.

Anyway, because i don't have a CD drive im pretty stuck with what to do next :s Any help would be great At the moment all i can get into is the bios, then the next screen, instantly, is the Error So im guessing i will need some sort of network boot disk to fix the MBR? I just don't know which ones or how to do it.

Oh, this was be partition set-up before **** hit the fan:
1) Windows
2) NTFS storage partition
3) Linux file system
4) Linux swap.

Im pretty sure the partition i deleted was the file system one, so not sure why its still flipping out.

---

### Post by logos34 on 2008-08-14
> to go into fdisk and delete the non-dos (linux) partition. All this did was change it from Error 17 to Error 18.

now grub can never boot ubuntu--you've deleted / along with the menu.lst it needs to access at boot 

can't you use BARTs to restore the windows bootloader? Other than that looks like you're SOL (unless you can boot from usb stick)

---

### Post by ...alex on 2008-08-14
I fixed it :D Just incase people are looking for a solution in the future...

I feel like a nub because i didn't know fdisk could do this... but i used Barts network boot disk to get to command prompt and ran FDISK /MBR and i was able to boot back into windows :D

Now i just have to figure out how to install Ubuntu without it shitting out. The only way i have been able to install it, is through Windows from the live CD, installing it to my C:\ drive. Installing it to any other partitioned drive, or using Unetbootin will screw it up.

---

