---
title: "Using Virtualbox to run an existing Ubuntu installation under Vista (Virtual Box)"
date: 2008-08-02
forum: General Help
---

### Post by Wake Rider on 2008-08-02
The setup of my hard disk is as follows:

sda1: Windows Vista Ultimate
sda2: Linux Swap
sda3: Gentoo Linux
sda4: Ubuntu

I would like to know how I can run Ubuntu and Gentoo in Virtualbox (or VMware etc I just remember that VMware server didn't support sound) under Windows Vista.

I know that linux users will be looking at me like I just ate a baby kitten, but I need Vista for my school work,(Windows will throw a hissy, with activation etc if a native partition is virtualized) and trying to learn Gentoo and having it compiling, or running Ubuntu ties up my computer.

I would like to be running Vista so I can do my schoolwork, while browsing the internet safely in Ubuntu, and experimenting with gentoo and increasing my knowledge of linux simultaneously.

Where can I find a guide on how to do this? Most guides focus on using Windows under Ubuntu, not vice versa.

I have trawled through the Ubuntu forums and searched the internet. Most articles to do with this topic are for Windows under Ubuntu rather than Ubuntu under Windows. Some of these articles look very complex, and I don't want to wreck my computer!

Your help will be greatly appreciated!:)

---

### Post by Wake Rider on 2008-08-02
I found these instructions which is a start, but I need more them in more detail as I only want to create a .vmdk of my ubuntu installation. 

> 9.9.1. Access to entire physical hard disk
While this variant is the simplest to set up, you must be aware that this will give a guest operating system direct and full access to an entire physical disk. If your host operating system is also booted from this disk, please take special care to not access the partition from the guest at all. On the positive side, the physical disk can be repartitioned in arbitrary ways without having to recreate the image file that gives access to the raw disk.
To create an image that represents an entire physical hard disk (which will not contain any actual data, as this will all be stored on the physical disk), on a Linux host, use the command
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
-rawdisk /dev/sda
This creates the image /path/to/file.vmdk (must be absolute), and all data will be read and written from /dev/sda.
On a Windows host, instead of the above device specification, use e.g. \\.\PhysicalDrive0.
Creating the image requires read/write access for the given device. Read/write access is also later needed when using the image from a virtual machine.
Just like with regular disk images, this does not automatically register the newly created image in the internal registry of hard disks. If you want this done automatically, add -register:
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
-rawdisk /dev/sda -register
After registering, you can assign the newly created image to a virtual machine with
VBoxManage modifyvm WindowsXP -hda /path/to/file.vmdk
When this is done the selected virtual machine will boot from the specified physical disk.

[http://ubuntuforums.org/archive/index.php/t-604000.html](http://ubuntuforums.org/archive/index.php/t-604000.html)

---

### Post by Jose Catre-Vandis on 2008-08-02
Is there a particular reason (other than setup and configuration so far) that you need to run the distros you have off your hard drive? Is dual/multi booting to tiresome? You would be better off installing your Linux distros inside virtual machines than trying to run of the hard drive. You can do what you say but may be asking for problems. Just setup VirtualBox on Vista and create new machines for Ubuntu and Gentoo. 

You could also try backing up all the files of each distro and then unloading them into an empty virtual machine setup for the specific distro. You will have some reconfiguration to do as the virtual hardware (graphics etc) will not be the same as your real machine.

Running OS's inside virtual machines as guests keeps them separate from the real machine as is highly unlikely to wreck you computer

---

### Post by Terry_Dodson on 2008-08-08
Would you have step by step instructions for that?  I am fairly new to Linux and doing it under Vista might help me get used to using it better.

---

### Post by Jose Catre-Vandis on 2008-08-10
Assuming you are on Vista

You will need ISO files of your distros on disk (you can use CDs but it is much slower) and also need to download the windows executable for Virtualbox from [www.virtualbox.org](www.virtualbox.org)

Install Virtualbox

Run VirtualBox

If you are at all unsure RTM, especially the early parts about installation and setup

Set up a new machine, following prompts for your distro, most of the defaults will do

Ensure you point the CDROM drive to your distro iso, so that when the new VM boots it picks it up.

Start the VM and your distro ISO should boot either to desktop (if live cd) or offer you install instructions

---

### Post by KingWilliam on 2008-09-23
> 9.9.1. Access to entire physical hard disk
While this variant is the simplest to set up, you must be aware that this will give a guest operating system direct and full access to an entire physical disk. If your host operating system is also booted from this disk, please take special care to not access the partition from the guest at all. On the positive side, the physical disk can be repartitioned in arbitrary ways without having to recreate the image file that gives access to the raw disk.
To create an image that represents an entire physical hard disk (which will not contain any actual data, as this will all be stored on the physical disk), on a Linux host, use the command
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
-rawdisk /dev/sda
This creates the image /path/to/file.vmdk (must be absolute), and all data will be read and written from /dev/sda.
On a Windows host, instead of the above device specification, use e.g. \\.\PhysicalDrive0.
Creating the image requires read/write access for the given device. Read/write access is also later needed when using the image from a virtual machine.
Just like with regular disk images, this does not automatically register the newly created image in the internal registry of hard disks. If you want this done automatically, add -register:
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
-rawdisk /dev/sda -register
After registering, you can assign the newly created image to a virtual machine with
VBoxManage modifyvm WindowsXP -hda /path/to/file.vmdk
When this is done the selected virtual machine will boot from the specified physical disk.

This really helped me to boot my native ubuntu partition in a virtualbox vm running on Winblowz. Thanks!

---

