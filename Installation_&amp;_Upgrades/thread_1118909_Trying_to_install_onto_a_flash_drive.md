---
title: "Trying to install onto a flash drive"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by Flexico on 2009-04-07
OK, I have this 8GB flash drive, and I want to partition 6GB for Ubuntu to boot from and 2GB for use as a traditional flash memory for Windows. However, when I tried to install Ubuntu using the LiveCD (I'm pretty sure that's the one I have), the installation failed. So I went back and tried "use entire disk" with the same results. Now the drive cannot be formatted either in Windows or Ubuntu, nothing can make use of it. What happened?

Oh yes, at one point I tried this tutorial: [http://www.lancelhoff.com/multi-partition-a-usb-flash-drive-in-windows/](http://www.lancelhoff.com/multi-partition-a-usb-flash-drive-in-windows/)
...but that BootIt program didn't work. (I tried it before and after the drive became non-responsive.)

---

### Post by upchucky on 2009-04-07
If you have ubuntu already installed to the hard drive you can
boot the pc normally with the flash drive in the usb port or you can boot the pc using the live cd with the flash drive in the usb port, you may be able to see what the flash drive shows up as during the boot cycle, if so then make note of it.

download this,

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh
```

somewhere in the file this creates, it will identify the device and what is on it.

post the results of this diagnostic here.

on the chance that the boot process chokes on the flash drive you may have to format it in windows with fat32, or create either a fat 32 partition or a ext3 partition to make it usable, gparted should work from the live cd.

---

### Post by Flexico on 2009-04-08
Thanks! This is what I got:

```

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

```

I have tried to format it with Windows XP and Vista, and they just say, "It cannot be formatted." In Ubuntu it does not seem to give me an option to re-format. It just says "cannot mount volume."

---

### Post by Flexico on 2009-04-14
When I tried "dmesg" or "dmesg | tail", a bunch of technical data fills the terminal, then it says,
```
[  405.852887] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 16 not in group (block 0)!
[  405.854759] EXT3-fs: group descriptors corrupted!

```

BIOS recognized it as "USB2.0 (USB 2.0)".

Windows Setup CD recognizes the drive as "7.6 GB", but says "no disk in drive", which makes no sense to me, since it's a flash thumb drive.

Below is the message Ubuntu gives me when I plug it in. Right now I'm done trying to boot Ubuntu from it,  just want it to work normally!

---

### Post by lindsay7 on 2009-04-15
Have you tried  to format with Gparted?

You can also try...If you get to a windows machine, this tool will clean and format the usb back to factory settings, HP USB Disk Storage Format Tool v2.1.8. Search for it on the internert.

Also look at [http://lexar.com](http://lexar.com) for a program called "bootit" it is free and will clean and restore a usb drive.

Here is the location   [http://files.filefront.com/lexar+usb+formatzip/;10112841;/fileinfo.html](http://files.filefront.com/lexar+usb+formatzip/;10112841;/fileinfo.html)

---

### Post by Flexico on 2009-04-15
Aha! I discovered that the reason I couldn't find the Gnome partition editor under System>>Administration was that it needed to be installed! Now everything is working wonderfully. :) Thank you for your time!

---

### Post by tamas305 on 2009-04-15
I did the exact same thing as you, as a Java programmer I needed Ubuntu and a functional fat32 portion for windows.

   - 5gb Ubuntu (ext3, swap)
   - 2gb fat32 (windows stuff)

Use a partitioner like [gParted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") and partition your USB drive, make the first partition the fat32 (the one with the lowest number),otherwise windows cannot read it. Then tell Ubuntu to manual install and install / file onto the ext3 partition that you made with gParted. Let it install and if everything went correctly then you should be set.

-tamas

---

