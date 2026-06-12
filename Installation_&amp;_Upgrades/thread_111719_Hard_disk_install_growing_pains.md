---
title: "Hard disk install growing pains"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by john_spiral on 2006-01-02
Hi,

My old sony vaio laptop (running Win XP Prof SP2) doesn't have a CD-ROM drive or a PCMCIA network card so I've reverted to using the "Installation/FromWindows -> The CD approach" method detailed below:

[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

I've downloaded the ubuntu CD iso and copied the contents to my c:\ubuntu dir. 

Rebooting the machine after the above setup gave me a black screen after selecting "Install Ubuntu", I've now solved this by using the latest version of grub for dos (0.4.1).

The installer now manages to boot but gets stuck on finding the CD-ROM:

"Detect and mount CD-ROM Installation step failed"

After this step I'm given a number of choices, one of them being able to launch a terminal session.

Does anyone have any suggestions of where I could go from here? 

thanks Johne

---

### Post by UbuWu on 2006-01-03
Here are the official instructions for installing from a harddisk:

[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s04.html](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s04.html)

---

### Post by john_spiral on 2006-01-04
Thanks for the link UbuWu,

do you think I could use the **INSTALL_MEDIA_DEV** Installer Parameter detailed in section 5.2.1 to show the installer where the installation files are?

> INSTALL_MEDIA_DEV

The value of the parameter is the path to the device to load the Debian installer from. For example, INSTALL_MEDIA_DEV=/dev/floppy/0

The boot floppy, which normally scans all floppies and USB storage devices it can to find the root floppy, can be overridden by this parameter to only look at the one device.

---

### Post by john_spiral on 2006-01-04
the **INSTALL_MEDIA_DEV=/dev/hda1** did squat (nothing).

I've taken a leaf from the USB installation and typed the below command in the shell during the install:

mount -t vfat /dev/hda1 /cdrom

it mounts fine, but it still wants to look for the CD-ROM after returning to the installer,speak about fixation!

I've even done a search on "/cdrom" within the install forum but it's turned up nothing?

mmmmmm any ideas?

---

### Post by UbuWu on 2006-01-04
Hmm strange... you should probably file a bug report about that, so the developers can fix that. How did you get the install files on your harddrive by the way?

---

### Post by john_spiral on 2006-01-05
:p I've got it going!! But I still need to clean up local drive for the partition process.

The [Installation/FromWindows]("https://wiki.ubuntu.com/Installation/FromWindows") wiki needs to be corrected, if you download the .iso leave it intact and say put it into your c:\ubuntu folder

Pop over to the ubuntu [archive]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current//images/hd-media/")
 and pickup the following files from the hd-media directory.

initrd.gz
vmlinuz

You will now have three files in the c:\ubuntu folder: initrd.gz, vmlinuz, ubuntu-5.10-install-i386.iso

all the other instructions on the wiki seem correct, my main correction has been the source of initrd.gz & vmlinuz files for the boot process and leaving the  the .iso as one file.

UbuWu I originally got my install files from the breezy CD off a fellow windows machine via a usb ethernet connector (not recognised for the neboot install).
Hence my long journey.

Once I've completed my install I'll have a look at updating/correctting the wiki the more eyes on my correction the better!

Thanks to those on the install from .iso thread for providing the correct boot files.

caio

Johne

---

### Post by jx2150 on 2006-11-04
If I want to do this and I already use grub, what lines would I need to put into grub and where would I put the files necessary for installation?

Thanks!

-Jx

---

### Post by john_spiral on 2006-11-08
create a folder in your boot directory with the .iso file and the
initrd.gz & vmlinuz files.

insert the following lines into your grub boot entry via the menu.lst file, in the below example I created a directory called xubuntu and placed all the above files into my 3rd partiton:

title       Xubuntu install
root        (hd0,2)
kernel      /boot/xubuntu/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd      /boot/xubuntu/initrd.gz

hope this helps

John

---

### Post by almostlinux on 2006-11-09
> **john_spiral said:**
> create a folder in your boot directory with the .iso file and the
initrd.gz & vmlinuz files.

insert the following lines into your grub boot entry via the menu.lst file, in the below example I created a directory called xubuntu and placed all the above files into my 3rd partiton:

title       Xubuntu install
root        (hd0,2)
kernel      /boot/xubuntu/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd      /boot/xubuntu/initrd.gz

hope this helps

John
Hi john_spiral,

Does this work with the edgy installer too? Coz here it fails at the "Search and find iso" step :(

---

### Post by john_spiral on 2006-11-11
did you get the initrd.gz & vmlinuz files from?:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

---

### Post by almostlinux on 2006-11-11
> **john_spiral said:**
> did you get the initrd.gz & vmlinuz files from?:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

yes, that's where I got the images from. It fails at finding the iso.

When I tried with the breezy/dapper images, it was able to locate the (edgy)iso, but the install won't proceed because of mis-matching kernel module versions.

---

### Post by john_spiral on 2006-11-12
Try the edgy iso with a edgy vmlinuz and a breezy initrd.gz.

any luck?

If this fails we might need to edit the edgy initrd.gz file to ref the correct .iso. If we get this woking it will solve a question I've seen buzzing around the forums for a while without a solution.

---

### Post by john_spiral on 2006-11-12
the above method didn't work for me.

---

### Post by almostlinux on 2006-11-15
Yes, I've tried multiple combinations (also with the dapper initrd.gz). It results in a kernel panic on boot.

The iso-scan documentation which is built into the hd-installer says it looks for all the files ending with '.iso' in filesystems it recognizes.  Now that it doesn't I've reported a bug:

[https://launchpad.net/distros/ubuntu/+source/iso-scan/+bug/71185](https://launchpad.net/distros/ubuntu/+source/iso-scan/+bug/71185)

Hope someone notices it  :-({|=

---

