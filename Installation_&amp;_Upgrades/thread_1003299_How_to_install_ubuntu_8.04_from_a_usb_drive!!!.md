---
title: "How to install ubuntu 8.04 from a usb drive!!!"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by brettsnowboards on 2008-12-06
This is THE EASIEST way to get to create a bootable USB drive to install Ubuntu from the USB stick.

For windows users

I pulled this how to off of the website:

Completely format USB drive.
 
Make sure you have an .iso file of Ubuntu 8.04 on your desktop

Unzip files from Ubuntu 8.04 Installation folder into root directory of drive. (Example F:)

Preparing the files and USB flash drive

    * First up, we need to format the USB stick in Windows - go into My Computer, right-click on the USB drive, and then click Format. When prompted, select FAT32 as the file system. Don’t use NTFS - it won’t work!
    * Download and install 7-zip []("http://www.7-zip.org/download.html"). It’s free and extremely useful, for this and anything else you might need to do with compressed files. It’s also open source, just like Linux, so that has to be a good thing. Get the latest stable version to be on the safe side - not the beta.
    * Download Syslinux [http://www.kernel.org/pub/linux/utils/boot/syslinux/]("http://www.kernel.org/pub/linux/utils/boot/syslinux/"), which is the bootloader we will be using to make the stick bootable. Just get the latest version in zip format, and extract it to the Desktop - right-click, select 7-zip, then extract to syslinux-7.1.1 (or whatever) and then rename that folder to “syslinux”.
    * Open a command prompt (on the Start Menu under Accessories, or run “cmd”) and cd to the syslinux folder:
    * cd Desktop/syslinux/win32
    * Run this command to install the syslinux bootlader to the thumbdrive:
    * syslinux -ma f: (where f: is the letter of your USB thumbstick)
    * Now we need to extract the Ubuntu ISO - Right click on the ISO file, and select 7-zip/extract to ubuntu-8.04…



Getting the USB drive prepared is complete.



The preparation is done! You should now have syslinux installed on your USB thumb drive, and a folder called Ubuntu-8.04-somethingorother on your Windows desktop. Now it’s time ot create our bootable Ubuntu LiveUSB Stick!

-

Putting it all together

    * Drag all of the files you just extracted from the ISO into the empty USB drive.
    * Move everything from the isolinux folder into the root of the drive. So, if your USB thumbdrive’s letter is F, as in our earlier example, move all the files from F:\isolinux\ into F:\
    * Rename the isolinux.cfg file to syslinux.cfg
    * Eject the drive, insert into the computer you wish to install Ubuntu onto, and boot! Shazam!

You may need to configure your BIOS to boot from USB, or at least go in there and change the boot order to try external drives first. It’s quite a simple process, but varies depending on your motherboard manufacturer, and so I can’t really go into it here.

Most modern computers will let you press F12 during the very first boot screen to select a temporary boot device - you should only need this once so that could be sufficient.


This guide was pulled off of this link ([http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/))


Thank you Team TeaBag!!!

---

### Post by brettsnowboards on 2008-12-06
This isn't sucky.  I accidentally voted that when I posted it hahaha I hope you all find this to be as useful as I did

---

### Post by BoDwayne on 2009-01-10
Well, that's fine as far as it goes, but how do I make a bootable USB from Ubuntu?  I gave up on Windows over a year ago.  
Does anybody know how to "burn" the Ubuntu ISO onto a flash drive so it can be used to do a Live install?  I'm having trouble getting a successful install CD made.


EDIT - I found my own solution.  I recently installed 8.10 on another machine, and discovered it has a built-in function under  System>Administration>Create a USB startup disk.

---

