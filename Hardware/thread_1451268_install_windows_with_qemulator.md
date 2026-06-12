---
title: "install windows with qemulator"
date: 2010-04-10
forum: Hardware
---

### Post by suoko on 2010-04-10
i have karmic installed and cause of some problems i don't know, windows doesn't boot anymore
i now downloaded winxp iso and want to install it but have no cd reader on my netbook
i then configured qemulator to boot from iso img and set hdd to /dev/sda3 which is my spare partition where i want to install windows but the error you can see in the attached image pops up

i tried without setting the hdd and it boots but hangs after a few seconds

how can i do what i want ?

i need windows for google skecth up only ...

i don't want to burn iso to usb pen, install windows and loose grub

---

### Post by suoko on 2010-04-10
installing now
i used 
qemu -hda /dev/sda3 -cdrom Scaricati/winxp.iso -boot d

had to press F6 and F2 at install and then continued skipping those options

---

### Post by suoko on 2010-04-10
windows seems not able to format the partition :-/
trying out osx now
qemu -hda /dev/sda3 -cdrom Scaricati/iDeneb_v1.5.1_OSX86_v10.5.7/iDeneb_v1.5.1_OSX86_v10.5.7.iso -boot d

---

### Post by srs5694 on 2010-04-10
Assuming /dev/sda3 is empty (or was your original Windows install that you're willing to trash), try this:

```

sudo dd if=/dev/zero of=/dev/sda3 bs=512 count=1000
sudo fdisk /dev/sda3

```

Once in fdisk, create one or more partitions for Windows (using the 'n' option, followed by 't' to change the type code to 07), then save the changes (using 'w'). At this point, /dev/sda3 will contain a valid MBR partition table, so it will look just like a hard disk to QEMU.

Another option might be to use WINE to run your program; however, I don't know enough about your program to know if WINE will handle it. Check the [WINE application database](http://appdb.winehq.org/) for information on that. In fact, using WINE is probably a superior option for running a single program, assuming it will actually run. It'll be quicker to launch, you'll get better integration into your desktop (you'll be able to cut-and-paste between the Windows program and Linux programs, for instance), and it'll be easier to save files from the Windows program in your regular Linux directory tree (you can do this in a virtual machine, but you need to set up networking tools to do it).

---

### Post by suoko on 2010-04-10
thanks
i used gparted however
the problem was ntfs
with the partition formatted as vfat i couldn't proceed with install

---

### Post by emanuel.b on 2010-04-10
Have you considered using VirtualBox? It works great for me. Been running XP for a while without problems...

---

