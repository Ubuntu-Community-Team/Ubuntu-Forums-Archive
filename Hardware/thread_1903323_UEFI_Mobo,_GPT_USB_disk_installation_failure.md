---
title: "UEFI Mobo, GPT USB disk installation failure"
date: 2012-01-02
forum: Hardware
---

### Post by nerasezi on 2012-01-02
Hi everybody
I've searched a bit on the web before posting the thread but i didn't come up with anything.
Here's my problem: Asrock H67M mobo with UEFI support and up-to-date to the latest firmware (1.70). I need to install Xubuntu 11.10 on an USB3 1TB hard drive, with GPT layout, no internal SATA HD. 
Here's what i've already tried but didn't work:

- Set as first primary partition, a FAT32 256 mb volume, boot flag "on" labelled as "EFI" with these directories "efi/ubuntu" ( tried also with "efi/grub" and "efi/boot" ) on it.
I was not able to create the "grubx64.efi" according to the Ubuntu UEFI guide: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) cause it keeps telling me to modprobe efivars, even when i did it as root hundreds of times.

- I've wipe down the hd, create a new gpt layout and partition table such as / volume and swap area. All primary partitions. So i installed the boot loader on the / partition (ext4) but nothing works.

- I wipe down the drive again and tried with MBR layout, boot flag on the / partition. When i boot up it didn't come up the warning that no boot volume was recognized, but stucks on a flashing underscore. 

Wipe down once again and create a brand new GPT layout partition scheme with no installation, which is the following:

FAT32 > 256mb > boot (recognized as EFI system partition)
EXT4  > 40gb
UNFORMATTED > 40 gb
NTFS > 800gb
SWAP > 4gb

Can someone please tell me step by step, what should i do to install the system from a live CD (64bit version)?
Since the GPT works a little bit different from MBR, where the h**l should i tell the isntaller to put grub when i have to select the target device? I've tried with "/dev/sda1" (the efi system partition) "/dev/sda2" (the ext4 / partition) but didn't work.

Last thing: a good source i've found is [www.rodsbooks.com](www.rodsbooks.com) but nothing.

It' driving me crazy

---

### Post by nerasezi on 2012-01-03
Any suggestion guys?

---

### Post by oldfred on 2012-01-03
I do not have UEFI, but hope to by summer, so I have been following suggestions and saving links. I have BIOS but use gpt on all my new drives. With gpt & BIOS you have to have a 1MB bios_grub partition, but with UEFI the first partition has to be the efi partition. You have already gone to the two sites I usually recommend. The rodbooks site is srs5694 in forum and I think skodabenz is the one on the arch site that knows UEFI.

EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)


There are some bugs.
UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

If you have it partially installed run this as the new version of boot script will also parse efi partitions.  Please post results.txt in code tags:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

Some threads where users did get UEFI to work:
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

### Post by nerasezi on 2012-01-04
I've read something on the Archlinux online help and it's very well written tutorial.
What i probably miss is the entire picture, cause i don't know how EFI exactly works. In my opinion MBR is a lot easier and i'd go for that if it'd work but it won't for me. Maybe is a bug on the mobo uefi firmware that Asrock will fix later on. 
The weird thing is that i successfully installed ubuntu 11.10 on a 8 gb usb pendrive, with GPT layout. No EFI System partition and no Swap area. Just a plain ext4 root partition.
Why does it not work on a USB hard drive?

I'll follow all the sources you've listed and see what i got.

Thanks oldfred.

---

### Post by carl4926 on 2012-01-04
I can't answer your question. But I'm a Admin at openSUSE and I was involved in a thread recently which contains info that I think might be interesting to you
It's a big thread, but worth a read.
Pay attention to info by @please_try_again
[http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/470470-help-getting-error-parted-magic.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/470470-help-getting-error-parted-magic.html)

---

### Post by oldfred on 2012-01-04
I have used gpt on a 16GB flash drive with a 8GB / (root) partition. I also created a small bios_grub and it installed without any issue booting with BIOS.

Several have reported that they cannot find a setting in BIOS/UEFI to choose boot mode. It must be that UEFI checks for the efi partition with 'boot' flag or gpt code of ef00 and then if not found it boots in BIOS mode using MBR.

Most from srs5694:
In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

I have had no issues creating gpt disks with gparted. 
If using gpt with BIOS create a 1MB bios_grub partition at the beginning of the drive. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

I would suggest to partition in advance. If using UEFI create a 200-300MB efi partition as the first. If in BIOS mode you may still want to leave the 300MB as a data or non efi partition, create a 1MB bios_grub partition and all the others you need. I think if dual booting with Windows it wants the second partition to be a Windows boot file partition. In BIOS the bios_grub partition can be anywhere on the drive.

---

### Post by nerasezi on 2012-01-09
I finally got it working guys. 

My main source was the Ubuntu UEFI guide: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) but the Archlinux tutorial helped as well.

That's what i did step by step.


1) Use a live CD which match the UEFI architecture. Mostly x86-64.
Boot up the live cd (xubuntu or lubuntu. Those are lightweight desktop but it should work with ubuntu and kubuntu as well).
Be sure your live system is booting in UEFI mode. You may check it on the UEFI setup, probably under Boot option or similar. In my case it just put the "UEFI" prefix before the device name.


2) Once the live system is running,to be more handful, i open the terminal, and set root password by

*sudo passwd*

Then i log out from the default live cd user and log in as root in gui mode.
Plug in the hard drive. I use a USB3 portable Hd but in most cases the hard drive is a SATA internal drive. Anyway, be sure you've BACKED UP ALL YOUR DATA, cause the process is going to wipe off everything on the drive.
Launch Gparted (a gui tool is much easier than the text one) and select the drive you're willing to install the system into. (Be sure to select the right one!)
Point to the top menu and select Device>Create Partition Table... A warning message pops out. Click on Advanced and select "gpt". Say OK
A new GPT disk layout had been created. 
Now you need to create partitions on it. It's very important that you create as the first and primary partition, a FAT32 volume and you need to assign the label EFI to it. Once the partition is created, right click on it and select "manage flags". Check the "boot" flag and say OK.
Move on to the creation of the / partition (you may want to separate /home and /boot. Do it as you usually do. In my case I've just created the / partition), and a swap area. Always prefer primary partitions cause with GPT the 4 primary partition limitation has been removed.
Close Gparted.

3) Install the system into the hard drive "/" partition and remember to point here the bootloader (GRUB 1.99) to install to. If you've created a separete "/boot" partition, you have to choose that one for the bootloader installation.

4) Here comes the part from the UEFIBooting guide:

**Building GRUB2 (U)EFI**

Download the latest grub2 source code ZIP file. [ftp://ftp.gnu.org/gnu/grub/](ftp://ftp.gnu.org/gnu/grub/)

Building grub2 requires the following programs to be installed (build dependencies):

bison
autoconf
automake
flex
autogen
python (2.x series) (for autogen.sh if building from bzr repo)
texinfo
help2man
gettext (NLS support)
device-mapper
freetype2 (libs)

*sudo apt-get install bison libopts25 libselinux1-dev autogen m4 autoconf help2man libopts25-dev flex libfont-freetype-perl automake autotools-dev freetype2-demos texinfo efibootmgr*

See i added "efibootmgr" to the software you need to install, cause you will need it later on.

For 64-bit (U)EFI:

*export EFI_ARCH=x86_64 ./configure --with-platform=efi --target=${EFI_ARCH} --program-prefix="" make*

In case you have a 32-bit architecture, check the online documentation at the link i provided at the top.

**Install GRUB2 in (U)EFI systems**

Determine your EFI SYSTEM PARTITION. (it should be /dev/sda1 or /dev/sdb1 if is set on the 2nd hd)

Then mount the partition at /mnt/EFISYS (or at any mountpoint you wish). The following code assumes /dev/sda1 to be EFISYS partition.
[I]
sudo mkdir -p /mnt/EFISYS

sudo modprobe dm-mod

sudo mount -t vfat -o rw,users /dev/sda1 /mnt/EFISYS

sudo mkdir -p /mnt/EFISYS/efi/grub[/I]

Then, build an EFI application for GRUB and copy it and the other modules:

Enter the "grub2 compiled source/grub-core" directory

*grub-mkimage -O ${EFI_ARCH}-efi -d . -o grub.efi -p "" part_gpt part_msdos ntfs ntfscomp hfsplus fat ext2 normal chain boot configfile linux multiboot*

*sudo cp grub.efi *.mod *.lst /mnt/EFISYS/efi/grub*

Note : The -p "" option is important for creating a portable grub.efi app. Now create a grub.cfg in /mnt/EFISYS/efi/grub :

*sudo touch /mnt/EFISYS/efi/grub/grub.cfg*

**Make the firmware launch GRUB2 (U)EFI as default**

_For non-Mac UEFI systems, *efibootmgr* is used to modify the UEFI Firmware Boot Manager._ This requires the kernel to be booted in UEFI mode and that the kernel processor architecture should match the firmware architecture (and 'noefi' is NOT used) for 'efivars' kernel module to be loaded and efibootmgr to access the boot manager variables. _Initially the user is required to manually launch "efi/grub/grub.efi" from the firmware console itself if grub2-efi was installed in BIOS mode. Then efibootmgr should be run to create the boot entry._

*sudo modprobe efivars*

Enter the "grub2 compiled source/grub-core" directory

*grub-probe --target=device /boot/efi/efi/grub/grub.efi*

Assuming the output the grub-probe to be /dev/sda1

*sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label "GRUB2" --loader "\\EFI\\grub\\grub.efi"*

In the above command, /boot/efi/efi/grub/grub/efi can be split up as /boot/efi and /efi/grub/grub.efi, which translates to (/dev/sda) -> partition 1 -> \\EFI\\grub\\grub.efi . 

HERE WHERE I GOT STUCK BEFORE AND HOW I SOLVED IT:

5) Open Synaptic and remove all grub packages and install just the grub-efi packages (amd64 for me) and all the necessary dependencies.
Once the installation is over, run *sudo update-grub* in the terminal. You should edit "grub.cfg" from /boot/grub and check that the disk UUID matches your disk and partitions, the voice "insmod part_" and "set root='(hd0," have "gpt" textline. If everything is ok, copy "grub.cfg" to the "efi/grub" on the EFI System Partition.
If something i mentioned before, doesn't match, just edit grub.cfg and manually change them values. Then copy the file to the "efi/grub" directory on the Efi System Partition (should still be mounted under /mnt/EFISYS).

Then when i rebooted the system, a new entry on the Boot tab under the UEFI setup has appeared, named GRUB2 and i set it as the default boot option.

I'm available for further explanation if anybody needs.

---

