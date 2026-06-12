---
title: "How to make a USB stick a DSL liveboot stick?"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by fINTiP on 2008-12-17
I've got a generic 1gig usb stick disguised in a pen, and want to make it a DSL live boot (though I'm open to suggestions about other live boot options?)

I've been using this guide from the wiki: [http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive](http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive)

I've also found [this]("http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl/") and [this]("http://linux.web.psi.ch/livecd/usbdisk.html") to reference.

However, I very quickly find I am over my head. First off, the torrent seems to have given me the .iso, so I'm working with that, and not the zip file mentioned. Listed in the tutorial (and the second reference link) is a method for extracting (?) the iso contents onto the USB drive, and I get very lost.

From the wiki:

> **#  Mount ISO image, with e.g. mount /tmp/dsl-3.2.iso /tmp/iso -o loop**
# Copy all contents from ISO to USB drive: cp -vr /tmp/iso/* /flash/
# Rename and move syslinux files to root directory: mv /flash/boot/isolinux/* /flash/
# Rename isolinux.cfg: mv /flash/isolinux.cfg /flash/syslinux.cfg
# Unmount USB drive: umount /flash
# Install syslinux: syslinux /dev/sdx1 and eventually set the MBR boot flag for this partition (with fdisk). 

How one can mount an iso unknown to me... I understand it's a disk image, made to be burned, but I have no idea how to handle them outside of burning them, and am afraid to blindly follow these instructions. I want to understand the process anyways.

I've already [wiped it]("http://sathyasays.com/2007/06/13/formatting-usb-pen-drive-in-linux-using-terminal/"), and then made it bootable with syslinux--I think? I followed instructions on that one and it seems fine. If you need me to check, simply tell me how... there is information on there about syslinux's requirements that I didn't understand, so this might well be worth doing.

Thanks for the help, I'm quite confused.

L

---

### Post by tgalati4 on 2008-12-17
There are several ways to do it.

One way is to boot with a live CD-which means you need to burn the dsl iso to disk.

Then use the system tools to install to USB drive.

---

### Post by shane8002 on 2008-12-17
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sintacto on 2008-12-17
in intrepid ibex and jaunty jackalope there is an option to make a bootable usb 
in 9.04 its system--administration--create usb start up disk.
but i think it was in applications--accessories--in 8.10 cant remember but i made one and it works
it can be improved (no swap space) not writing to it so much, etc.
I do like dsl specialy in dsl=toram mode.

---

### Post by fINTiP on 2008-12-17
I don't want to make an ubuntu live boot, but a Damn Small Linux (DSL) live boot. That aside, I'm in 8.04, though those options sound neat.

There isn't going to be a 9.04, is there? It should go to 9.10, shouldn't it? .04 indicates lts, and those are every three years... hardy hasn't even been out for one year.

In other news, I actually saw an Ibex in person the other day. They make the queerest noise.

----

Also, I don't have a cd burner... that's really inefficient, anyways, though, and less educational! :)

Anything else?

Thanks for the quick responses.

L

---

### Post by fINTiP on 2008-12-17
Went ahead and tried the instructions... everything seemed to go smoothly, but I got a "boot failed" screen when I tried to boot it on my friend's 1.8ghz IBM Lenovo thinkpad.

I'm wondering if it's an MBR problem? I wiped the drive and am following the instructions I listed in my first post from scratch... if it still doesn't work, I'll try wiping and replacing the MBR, but I understand very little about that. If someone wants to expand upon these instructions, I'd be grateful:

>  Optional: Replacing MBR

If you need to wipe the MBR on the Flash Disk, do it with a command like below. This shouldn't be necessary unless there's another funky bootloader in the MBR (like, if you were experimenting with another bootable USB linux distro). BE *VERY* CAREFUL NOT TO WIPE YOUR HARD DRIVE'S MBR HERE!!! Replace sdX with the path to your USB drive

   dd if=/dev/zero of=/dev/sdX bs=446 count=1

Here are two ways to replace MBR
    Using 'mbr.bin' from Syslinux: 

   locate mbr.bin
   cat /somepath/share/syslinux/mbr.bin > /dev/sdX

    Using ms-sys:

        Install [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/) and put another MBR in its place: 

   ms-sys -s /dev/sdX


ALSO:

I notice that at this step, there is a slight discrepancy:

Rename and move syslinux files to root directory: mv /flash/boot/isolinux/* /flash/

I don't have a "/boot" directory in the drive's root directory--isolinux is just in the root directory already.

This leads me to question what version I am using? The iso I have is called dsl-n-01RC4.iso; anyone know how to tell what version that is?

K

---

### Post by fINTiP on 2008-12-17
A second look revealed that the isolinux.cfg file was actually in the folder /media/DRIVE/isolinux, and that I needed to move **this** file to the root and rename it, which I have done...

now I've followed the steps, and also realize that the second part of the last step last time: how does one set the boot flag with fdisk? I'm looking it up, and it seems that it's with the -flag option, but I have no idea how to use fdisk at all, or even what that program is useful for.

L

---

### Post by pastalavista on 2008-12-17
The easiest way I've found to make a bootalble, live, USB/flash drive of almost any distro out there is with [unetbootin]("http://unetbootin.sourceforge.net/"), but I have a fast net connection. If you have one, just download unetbootin, run it, and in the first drop-down menu select Damn Small Linux. Be sure your flash drive is plugged in and doesn't have anything else on it and then in the last drop-down select USB. It will download and install to the thumb drive while you sit back and twiddle your thumbs.

---

### Post by iponeverything on 2008-12-17
> I don't want to make an ubuntu live boot, but a Damn Small Linux (DSL) live boot. That aside, I'm in 8.04, though those options sound neat.

That tool works with any bootable ISO.

---

