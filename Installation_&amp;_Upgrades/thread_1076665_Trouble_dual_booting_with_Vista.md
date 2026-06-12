---
title: "Trouble dual booting with Vista"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by artgoi on 2009-02-21
Hello everyone,

Im using 8.10.
Ive succesfully installed it on a separate partition from my Vista install. However, Id like to have Vista as my primary bootloader. So, using Easy BCD, I tried to install the neogrub boot loader, but have failed. This is what it looks like:

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fce41dff-71b1-48cd-b44a-6368c7381387 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fce41dff-71b1-48cd-b44a-6368c7381387 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin



So far, I get Error 19. Im not sure which root it is. I put (hg0,1) because in Vista on the disk management, it is the second partition.

What should I do? Would a reinstall be easier? I dont have anything on Ubuntu yet so, Im open to the easiest way to do this.

Thanks!

---

### Post by TimDaniels on 2009-02-22
> **artgoi said:**
> Hello everyone,

Im using 8.10.
Ive succesfully installed it on a separate partition from my Vista install. However, Id like to have Vista as my primary bootloader. So, using Easy BCD, I tried to install the neogrub boot loader, but have failed. [......]

Real men don't use EasyBCD.  Instead, they use the Vista command line tools. :D

I wanted to add Ubuntu as a dual-boot with a pre-installed Vista, and I wanted to keep Vista's boot manager as the primary load control.  I made a compilation of various articles on the subject, and I ended up with a Vista boot menu that included the Ubuntu boot manager (Grub) as an option and an Ubuntu boot menu that included Vista's boot manager as an option.  Thus, one could go from one boot manager to another before making one's mind up on which OS to load.  It was a year ago that I did it, so don't expect me to know than what is written here:

---------------------------------------
DISTILLATION OF SEVERAL ARTICLES -
USING BCDEDIT TO ADD A LINUX ENTRY TO VISTA'S BCD STORE
-------------------------------------------------------

Install Grub to Linux partitiion (not to MBR)

in Ubuntu:

find device names of Vista(VV) and Linux(LL) partitions
  System/Preferences/Hardware Information/SCSI Adapter [CANNOT FIND]
or
  sudo fdisk -l

copy the boot sector of the Linux partition
  directly to the root of the Vista partition
(check the name of the Vista partition in /media)
  sudo dd if=/dev/sdLL  of=/media/sdVV/Ubootsect.bin  bs=512  count=1

Use Synaptic to load Gparted from installation DVD,
mark Vista partition "active" to load Vista's BCD
  [use Gparted's "Manage flags" to set the "boot" flag]

  System/Administration/Partition_Editor
or
  sudo gparted


in Vista:

rt-click command prompt icon, select "Run as administrator",
show the current boot menu entries
  bcdedit /enum

(if there is already an obsolete entry for Ubuntu,
 delete it with:  bcdedit /delete {obsoleteID}     )

in Vista's command prompt, make a new BCD entry
  bcdedit /create /d "Ubuntu" /application BOOTSECTOR

  [rt-click|Mark, highlight "{long hex no.}", rt-click]
  [refer to the returned long hex no. as "UbuntuID"]

declare the ID as a boot device
  [rt-click|Paste to fill in "{UbuntuID}" in cmd below]

  bcdedit /set {UbuntuID} device boot
  [including the braces]

specify the path to the copy of the Ubuntu boot sector
  bcdedit /set {UbuntuID} path \Ubootsect.bin

add Ubuntu entry to the boot time menu
  bcdedit /displayorder {UbuntuID} /addlast

set default OS timeout to be 10 seconds
  bcdedit /timeout 10

show the new boot menu entries
  bcdedit /enum

in Ubuntu, edit boot menu
  sudo gedit /boot/grub/menu.lst
--------------------------------------

It worked for **me**.  I expect that it will work for you, too.

*TimDaniels*

---

### Post by caljohnsmith on 2009-02-22
If you would like specific help configuring NeoGrub to boot Ubuntu, it would help to first get a clearer picture of your setup; how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

