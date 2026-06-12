---
title: "Boot problem"
date: 2009-10-15
forum: Hardware
---

### Post by earthmumma on 2009-10-15
Hi,

when I try to start Kubuntu I get the GRUB list, I select recovery mode (or any other) and I get the following message:

> Boot from (hs1,0) ext3  [then a serial number]

Error 16: Inconsistent filesystem structureIve tried loading the Live CD and mounting a drive but all devices can't be mounted.

please help

thanks:confused:

---

### Post by Niko Johnson on 2009-10-15
you can try to edit your boot options... when grub loads press e to edit the partition you would normaly boot from then at the end of the line of code type "single" without quotes this will tell kubuntu to boot in single user mode only giving you the command line interface. then when you get in the terminal check your grub options. i find it weird that your booting from hs1 instead sda1 but i can be wrong.. you can check your grub file in the /boot/grub/menu.list file. change that to fit your needs and make sure you booting off the right partition

---

### Post by Giblet5 on 2009-10-15
At the boot menu, select the normal option but DON'T hit Enter.

Hit the 'e' key.

Highlight that (hs1,0) and hit the 'e' key again.

Change the 's' to a 'd' so that it reads (hd1,0) (aka hard disk 1, partition 0).

Hit Enter, then hit 'b' and Enter.

If it boots correctly, log in and bring up a terminal window. Run this command: ```
sudo fdisk -l | head
```
We'll assume that the first disk device listed is /dev/sda:
```
sudo update-grub
sudo grub-install /dev/sda
```

Work as you normally would. The system should boot correctly from now on.

---

### Post by earthmumma on 2009-10-15
sorry - should have written hd1, hs1 was a typo.

when I hit e I get the following options

> uuid [serial number]
kernel /boot/vmlinux-2.6.31-13-generic root=UUID= [serial number]
initrd /boot/initrd.img-2.6.31-13-generic
quiet

i added single to each one of them and hit 'b' and I get:

 Error 15: File not found...

cheers

---

### Post by Giblet5 on 2009-10-15
> **earthmumma said:**
> i added single to each one of them and hit 'b' and I get:

 Error 15: File not found...
cheers

OK, do you know which drive Linux is installed on?

The partitions can be 0-4 and the drive is likely 0 or 1...

If all else fails, here's [how to fix it]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") from a Live CD.

That link assumes that the problem is because of installing Windows, but the process is the same; it should work fine.

---

