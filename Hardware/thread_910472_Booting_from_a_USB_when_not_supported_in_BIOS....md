---
title: "Booting from a USB when not supported in BIOS..."
date: 2008-09-04
forum: Hardware
---

### Post by Jaeric on 2008-09-04
Hello all.  This is not an ubuntu specific question so I hope it is ok to submit it here.  Perhaps there might be an ubuntu related answer.

I have a Dell Latitude CPI A-series laptop that I received when a relative upgraded their laptop.  I thought this would be a perfect candidate to try xubuntu or any other light Linux distro on.  It has a little under 100mb of ram a Pentium II and a 4gig harddrive.  When I received it, it was running Win2000 horribly.  I then immediately reformated the computer.  After that, I realized, due to the fact that the floppy and cd drives had to be swapped, that the cd drive was shot, probably in transit.  My question is:  Is there a known floppy install, say DSL or something that I could install via the floppy drive or is there a method to get it to boot from USB even though BIOS does not support a USB boot?  Basically, is there any way short of getting a new cd drive to get a linux OS on this laptop.

I have tried the solutions mentioned on the pendrivelinux.com website to no avail.  Here are what they offered:

[http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/)

[http://www.pendrivelinux.com/2007/11/04/usb-pendrive-linux-install-from-windows/](http://www.pendrivelinux.com/2007/11/04/usb-pendrive-linux-install-from-windows/)

Thanks for your time and any help is appreciated. :guitar:

---

### Post by IntuitiveNipple on 2008-09-04
Does it have an Ethernet network port? Do you have a small LAN to connect it to? If so, do some research on PXE (Preboot eXecution Environment) boot.

Here's a start for you: "[How To Configure PXE (Network) Booting on Ubuntu For Network Based Installations](http://ubuntu-tutorials.com/2007/10/11/how-to-configure-pxe-network-booting-on-ubuntu-for-network-based-installations/)"

---

### Post by snowpine on 2008-09-04
Hi Jaeric, I believe you can put Grub on a floppy and then use that to boot from the USB--thankfully I have never had to do it, so I have no personal experience! :) Another solution I've heard of is to put the hard drive in another (working) laptop, install the OS, then switch the hard drive back.

Why am I posting on your thread if I don't have a solution? Because I want to warn you against installing Xubuntu on that machine. It is just too "heavy" for your hardware. You're into DSL territory. :) Here's some reading material:
[http://ubuntuforums.org/showthread.php?t=478237](http://ubuntuforums.org/showthread.php?t=478237)
[http://ubuntuforums.org/showthread.php?t=250161](http://ubuntuforums.org/showthread.php?t=250161)

---

### Post by Jaeric on 2008-09-04
Intuitive, first off, I love your username..lol

Thanks for the info.  Unfortunately, this laptop does not have a ethernet port or a modem for that matter.  I do have a card that has a 56k modem, but I do not know that that will work for what you are suggesting.  I will look into the link you added and see how feasible it will be.

---

### Post by Jaeric on 2008-09-04
> **snowpine said:**
> Hi Jaeric, I believe you can put Grub on a floppy and then use that to boot from the USB--thankfully I have never had to do it, so I have no personal experience! :) Another solution I've heard of is to put the hard drive in another (working) laptop, install the OS, then switch the hard drive back.

Why am I posting on your thread if I don't have a solution? Because I want to warn you against installing Xubuntu on that machine. It is just too "heavy" for your hardware. You're into DSL territory. :) Here's some reading material:
[http://ubuntuforums.org/showthread.php?t=478237](http://ubuntuforums.org/showthread.php?t=478237)
[http://ubuntuforums.org/showthread.php?t=250161](http://ubuntuforums.org/showthread.php?t=250161)

Thanks!  You are probably right about xubuntu.  I will look into the links you added.

---

### Post by IntuitiveNipple on 2008-09-04
If you've got another PC to work from, then how about simply removing the hard drive from the laptop, connecting it to the PC with a suitable cable-converter, and then creating the bootable image on the hard disk by mounting it in a virtual machine (VM) and booting the VM from a .iso CD image and installing from the CD?

When it's done and tested in the VM simply move the hard disk back to the laptop and off you go.

---

### Post by Jaeric on 2008-09-04
> **IntuitiveNipple said:**
> If you've got another PC to work from, then how about simply removing the hard drive from the laptop, connecting it to the PC with a suitable cable-converter, and then creating the bootable image on the hard disk by mounting it in a virtual machine (VM) and booting the VM from a .iso CD image and installing from the CD?

When it's done and tested in the VM simply move the hard disk back to the laptop and off you go.

That is a good idea and one I have not heard of.  The only problem I forsee is the lack of a proper cable-converter.  I guess it comes down to how much I am willing to invest in getting this PC going.  Is there a means of converting a regular IDE cable to work for such a thing?  Well, even still there is the power issue...

All good ideas.  Seems there is a few more ways to skin this cat.  Just a matter of time and money I suppose.

---

### Post by IntuitiveNipple on 2008-09-04
> **Jaeric said:**
> That is a good idea and one I have not heard of.

I've written several automated scripts to create VM images using chroot and disk image files. The only difference here is using a real disk device rather than a /dev/loop device. The script takes about 10 minutes to run, depending on the speed of the Internet connect.

Tha method is probably better than trying to install from a CD since you want a system that has the smallest memory and disk footprint possible. Get it going with a console installation and then add to it as you work out what it can usefully support.

> **Jaeric said:**
> 
 The only problem I forsee is the lack of a proper cable-converter.  I guess it comes down to how much I am willing to invest in getting this PC going.

As an example here's an [IDE to 2.5" Laptop Hard Disk cable](http://www.overclock.co.uk/product/Value-IDE-TO-2.5inch-Laptop-Hard-Disk-Adaptor-Cable_4225.html) - I'm sure you can find one locally.

---

### Post by Jaeric on 2008-09-04
> **IntuitiveNipple said:**
> I've written several automated scripts to create VM images using chroot and disk image files. The only difference here is using a real disk device rather than a /dev/loop device. The script takes about 10 minutes to run, depending on the speed of the Internet connect.

Tha method is probably better than trying to install from a CD since you want a system that has the smallest memory and disk footprint possible. Get it going with a console installation and then add to it as you work out what it can usefully support.


As an example here's an [IDE to 2.5" Laptop Hard Disk cable](http://www.overclock.co.uk/product/Value-IDE-TO-2.5inch-Laptop-Hard-Disk-Adaptor-Cable_4225.html) - I'm sure you can find one locally.

Sweet.  That just might be the ticket.  I will look into getting one of those nifty cables and then trying out one of the scripts you mentioned.  Thanks!

---

### Post by Jaeric on 2008-09-06
Ok, I have found a solution to my problem.  In a word, Puppy!  Puppy Linux had everything I needed for this problem all of which were automated tasks.  All I needed to do was supply the media and answer the prompts accordingly.  

Here is the primary source of the info I obtained:
[http://www.puppylinux.com/flash-puppy.htm](http://www.puppylinux.com/flash-puppy.htm)

The only issue I had was wakepup2 was unavailable from the Puppy 4/Dingo live CD from some reason.  With a little searching on the web I found a boot image of wakepup2 and wrote it to my floppy.  Here is the location of the image:  [http://files.filefront.com/wakepup2iso/;8971866;/fileinfo.html](http://files.filefront.com/wakepup2iso/;8971866;/fileinfo.html)
Just mount the iso and copy the .img file off the mounted cd image.  Then write it to a formated floppy.  

Pop in the floppy and the USB to your PC and go!  From that point you can run the Puppy Universal Installer and install it to your hard drive.

---

