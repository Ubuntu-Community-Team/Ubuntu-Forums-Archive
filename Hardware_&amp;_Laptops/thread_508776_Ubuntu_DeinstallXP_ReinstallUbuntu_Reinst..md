---
title: "Ubuntu Deinstall/XP Reinstall/Ubuntu Reinst."
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by mountainrider on 2007-07-24
I'm new to this forum and really hope somebody can help out. I just purchased a Compaq laptop used (EBay) with AMD 64 3200+. The laptop came with UBUNTU installed...no Windows. I was pleased because I have an interest in UBUNTU (have 7.04 disk already), but need to install a "dual boot" with Windows for software purposes. It was suggested by the seller that I simply reinstall Windows then reinstall UBUNTU. I decided to do just that using Compaq recovery disks (we have another Compaq LT)...but Windows hung on the final reboot (3rd disk) with the following message sequence:

GRUB loading stage 1.5.

GRUB loading, please wait...

Error 17

Obviously GRUB did NOT deinstall when XP reformatted. Now it won't even read an UBUNTU 7.04 disk to reinstall. I have adjusted the boot order (setup utility seems dated actually), attempted various bootdisks, "Boot 'n Nuke" etc, but I cannot get past the above error code! Sad( Any ideas? It will not read ANY disk at boot now. Help!!! Please?  Thanks!

Doug

---

### Post by mismis on 2007-07-24
I think ur problem is from the cdrom, try a diffrent one or try other boot options like floppy disk or usb. :)

---

### Post by BDNiner on 2007-07-24
Well if you computer is starting to load grub then there is something wrong with your boot from CD option in your BIOS. There is a key you can press during POST to select your boot device, on my computer it is F2. Try using that and selecting the CDROM drive. If it still loads grub then there is a problem with your cd rom drive. Try and switch it with the one from your other computer and then try to boot from cd.

You can also take the hard disk out and use a USB enclosure to attach it to the other computer and delete all the partitions, then run FDISK to completely clean up the drive, sometimes windows can't see all the Linux partions. Also if you have a MAC handy, use the external enclosure to format the drive, and then format it again when installing windows.

As a last resort you can update your BIOS and see if you can boot from CD after that. I hope something in here helps. Good luck.

---

### Post by mountainrider on 2007-07-25
Thanks...no floppy and USB booting is not an option with this particular BIOS.  As far as F2 key...no response. This is a Compaq and I suspect this function is superseded by BIOS/hardwired choices that appear on-screen such as "Press F10 for setup"...none of which have helped.  I have tried several software approaches such as canceling a Windows recovery install before completion...which dumps you to DOS.  I'm a DOS veteran but no approaches I have tried have succeeded in purging GRUB...which I'm fairly sure Windows/DOS will not recognize since it is on an "allocated" portion of the disk.  Nevertheless I am going to try to outflank it by attempting a Win 98 install f/b XP if it takes.  I may indeed have to figure out how to hook up to my desktop...hopefully with a simple extension ribbon cable if it exists...and do a complete format with that 'puter in control.  No matter what my first taste of UBUNTU has been disappointing. :(

---

### Post by mountainrider on 2007-07-25
Ah...we have joy...I successfully installed Win 98 (more complete HDD format apparently) and THEN successfully installed XP.  Thanks for your suggestions. :)

---

