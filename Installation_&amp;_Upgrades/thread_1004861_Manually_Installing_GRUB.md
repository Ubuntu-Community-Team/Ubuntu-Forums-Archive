---
title: "Manually Installing GRUB"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by dangreaves on 2008-12-07
Hey,

I am in the process of installing Ubuntu Server 8.10 on a desktop machine using a USB Drive prepared using the UNETbootin tool.

I have run the installation successfully but however experience the following problem when the installer attempts to install the GRUB Bootloader.

It automatically installs the bootloader to hd0 which - at the time of the installation - is the USB drive that the installer is running from. So in other words, it installs the bootloader on the wrong drive.

Is there a way of running the installation in command line mode (there is an option on step 1 of the installation) and then running a command to install grub to a specified drive.

Help extremely appreciated,
Dan

---

### Post by inobe on 2008-12-07
hi, when you get to the final step in the setup' i believe you have an advanced option button, it should allow you to install the bootloader on that usb drive, the option is there, you have to eye ball it.

edit: i just noticed you are using a non cd method, i am uncertain that you will get that option.

---

### Post by dangreaves on 2008-12-07
I have another idea that I think will be easier. If I run a live-cd (located on a USB drive) of Ubuntu Desktop 8.10 and run a console - what would i have to type to install GRUB on hd3 (the drive that Ubuntu Server is installed on).

Cheers,
Dan

P.S. That option isn't available, it just go's straight in all guns blazing "Installing GRUB to hd0". I also have to re-prepare the USB Drive every time as the installation of grub onto it messes it up.

---

### Post by inobe on 2008-12-07
just guessing, i would either disable other hard disks in the bios' or even disconnect them.

you could also use the super grub cd !

---

### Post by caljohnsmith on 2008-12-07
If you can't change Grub from installing to (hd0), then you could go ahead and let it do that, and then afterwards reinstall Grub to your USB drive and also to your Server drive so that they point to the correct partitions on their respective drives for Grub's boot files. If you want a hand doing that, how about first posting:
```
sudo fdisk -lu
```
And please identify the partitions. We can work from there if you want. :)

---

### Post by dangreaves on 2008-12-08
The problem i have is all due to booting from the USB drive rather than a disc. If it was installed from CD it would be fine.

I had the bright idea of running a live CD (from USB) of Ubuntu Desktop to access a console and try and sort it out from there only to find that the live-cd wont work from USB.

My partitions are as follows (according to Ubuntu Server at time of installation).

> > SCSI1 (0,0,0) (sda) - 1.0 GB Removable Disk
>> #1 primary 1.0 GB fat16

> SCSI1 (0,0,1) (sdb) - 1.6 MB Removable Disk
>> #1 primary 1.6 MB

> SCSI2 (0,0,0) (sdc) - 80.0 GB ATA ST380011A
>> #1 primary 78.5 GB ext3
>> #2 logical 1.5 GB swap

As you can see, the top two devices are the removable disk that the installer is infact running from (for some reason it is always listed as two devices). The bottom device is my harddrive.

My problem is that during the installation when GRUB is to be installed, the installer automatically writes to the MBR on the first device (the removable disk) rather than the third device (my HDD).

Is there any way that I can change the order of the devices?

Thanks,
Dan

---

### Post by caljohnsmith on 2008-12-08
I don't know of a way to change the order of devices, and since you can't find a way to change where Grub is installed during the installation process, how about doing the following commands to install Grub to your server sdc drive:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
Then if you boot the server sdc drive, you should get the Grub menu. If you have any problems booting Ubuntu from the Grub menu (you might get a Grub error 17 for example), let me know and we can work from there.

---

### Post by lovelyvik293 on 2008-12-08
Hai check it out:-
[http://ubuntuforums.org/showthread.php?t=235753](http://ubuntuforums.org/showthread.php?t=235753)

---

### Post by dangreaves on 2008-12-08
Where would I run those commands from? and I can't actually boot from my hard drive atall because there is no MBR installed on it as the MBR gets installed on the removable drive.

---

### Post by lovelyvik293 on 2008-12-08
You can run the commands while working with live cd.

---

### Post by caljohnsmith on 2008-12-08
Can you install the Live CD to your USB drive with Intrepid's new System > Admin > Create a USB startup disk? Or if you can't do that, you could install the Live CD to your USB via a program called "UNetBootin", and here's a [tutorial]("http://maketecheasier.com/how-to-boot-install-ubuntu-ibex-from-a-usb-thumb-drive/2008/09/22"). How about trying either of those methods and let me know how it goes.

---

### Post by dangreaves on 2008-12-09
Woo cracked it :D

I did the following:

> Install Ubuntu Server using unetbootin from USB
> Let the installation write to the wrong MBR
> Boot Ubuntu Desktop Live-CD using netbootin from USB
> Run the following from a console:

> sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

Note: For some reason, the live-cd defines my hard drive as hd0 rather than hd2 like the server installation did. This just takes some experimentation to find the right drive number.

And that was it, removed the drive, restarted and it booted perfectly. Now running a great dedicated web server of my own.

Cheers for the help guys,
Dan

---

