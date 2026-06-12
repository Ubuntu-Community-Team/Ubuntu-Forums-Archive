---
title: "kramic Rc and dedicated grub partition"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2009-10-23
I have a dedicated grub partition for my multiboot system. I have downloaded the kramic release and will do a fress install after backing my data. 
My concern is that keeping in mind the existing grub version is older that what is for kramic and a known issue wirh grub

"[COLOR="Teal"]Other OS options not shown in boot menu when installing with Ubuntu 9.10 RC
After installation from the Ubuntu 9.10 Release Candidate, other installed operating systems are not correctly displayed in the boot menu.(456776)[/COLOR]"

will i need to take extra care to update/redo the dedicated grub partition or some thing other than "[COLOR="DarkGreen"]run sudo update-grub from the commandline after rebooting[/COLOR]"

---

### Post by richlyn9 on 2009-10-23
i have already installed the kramic RC and rebooted after which the MBR still gave options for the old 9.04 version to boot and when i selected that it said  something not found.
i booted to my live CD and run these commands and it gave me this result

buntu@ubuntu:~$ grub-install
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-mkdevicemap=FILE use FILE as grub-mkdevicemap
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specified by
--root-directory, and uses grub-setup to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ 


i checked the menu.lst in the dedicated grub partition and found that it stilll has entried of the old install meaning it has not been updated.

Please help!!

---

### Post by richlyn9 on 2009-10-23
now i wonder if i simpy could update my existing intrepid to grub2 and also update the dedicated grub partition with the new version to get rid of troubles.
Also i cannot open ext4 partition from inrepid on ext3 system can i reinstall 8.10 with ext4?

---

### Post by richlyn9 on 2009-10-24
I have updated 8.10 with grub2 and updated the dedicated grub partition with grub2 as well however when i boot to my pc i directly gets to the grub prompt ssh:grub>
what next?

please advise..

---

### Post by meindian523 on 2009-10-26
Nevermind. Do you mean 9.10?

---

