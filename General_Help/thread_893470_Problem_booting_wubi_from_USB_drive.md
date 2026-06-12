---
title: "Problem booting wubi from USB drive"
date: 2008-08-18
forum: General Help
---

### Post by andrewcmcardle on 2008-08-18
My setup is a bit convoluted so bear with me

I installed wubi onto my Vista PC, then rebooted the PC to finish the wubi install in Ubuntu. I then rebooted into windows and copied the C:\ubuntu folder to the root of my usb pen drive. I then installed Grub4Dos (grub.exe) onto the root of the drive. I then used syslinux on the USB drive to make it bootable.

I then inserted the pen drive, set the bios to boot from USB drive and booted the computer. When the syslinux prompt came up saying that it cant find a kernel i typed in grub.exe and the grub menu opened up. I then entered the grub command line and entered the following commands

```
root (hd0,0)
configfile /ubuntu/disks/boot/grub/menu.lst
```

I then changed the first boot option so the first command was changed from

```
root (hd0,2)/ubuntu/disks/
```

to 
```

root (hd0,0)/ubuntu/disks/
```

i then run the boot command and the ubuntu splash screen appeared, then it all goes wrong, i get a busybox initramfs command line, but no ubuntu.

Does anyone have any idea what is going wrong? It's all ok until i reach the busybox.

---

### Post by Orlsend on 2008-08-19
Initramfs Usually means erros with the HD or a bad shut down I doubt this is the case since you are trying to boot from a Pendrive... Is is formated NTFS or FAT?

---

### Post by andrewcmcardle on 2008-08-19
The drive is formatted FAT32 as syslinux doesnt work on a NTFS drive. The infuriating thing is i have got this setup to work before, but i lost the usb drive and cant remember how i did it. I think i had to add some commands to the end of the "kernel" command in grub, this made it work properly.

---

### Post by andrewcmcardle on 2008-08-19
I have made some developments. I changed the value in the kernel boot command from root=uuid=(lots of letters and numbers) to root=/dev/hda1. This time when i boot the computer all goes fine untill the error
```

assuming drive cache: write through

```
appears and the computer stops booting up. Any idea what i should do next?

---

### Post by minhmeoke on 2008-08-19
Are you trying to install Ubuntu onto a USB drive? In that case, it is much easier to use UNetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) which will automate the process for you.

---

### Post by andrewcmcardle on 2008-08-20
I cant use UNetbootin as it doesn't make Ubuntu persistent, so my changes aren't saved. In wubi the changes are saved.

---

### Post by moycano on 2008-08-21
After successfully install a full Xubuntu system on a 2.0GB Flash drive, I noticed Windows can't natively read more than one partition and then remember I want exactly what you are trying to achieve.

I already add a ticket in ubuntu's brainstorm and I going to refer this topic:

[http://brainstorm.ubuntu.com/idea/12558/](http://brainstorm.ubuntu.com/idea/12558/)

SALUDOS/REGARDS.

---

