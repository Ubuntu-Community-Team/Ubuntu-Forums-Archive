---
title: "Installation onto bootable USB"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by dextras13 on 2009-04-19
I am trying to install Ubuntu 8.10 onto a USB as a bootable OS, that saves settings. This is what I've tried and done so far:

1. Used unetbootin (windows) to install .iso of Ubuntu 8.10 onto my Kingston 4GB USB.

2. Changed BIOS settings to boot from USB, then CD, then Hard Drive

3. Step 1 worked perfectly except for the fact that it didn't save the settings.

4. Tried [http://www.winmatrix.com/forums/lofiversion/index.php?t20558.html](http://www.winmatrix.com/forums/lofiversion/index.php?t20558.html) to make the USB save settings. It came up with errors.

How can i have a bootable Ubuntu USB that saves settings? I've been searching the internet for a while now but haven't come across any other solutions.

Thanks dextras13

---

### Post by snowpine on 2009-04-19
Unetbootin is not supposed to save your settings; it creates a "live" usb (like a live cd). 

Try System->Administration->Create a USB Startup Disk.

---

### Post by dextras13 on 2009-04-20
That worked so thank you but I have another question.

I need to be able to use my USB as a normal USB as well as for this. Is there a way to, when in XP when i double click on my USB drive for it to NOT auto open up the installation menu for Ubuntu? THis means that then I can actually save stuff n the USB with out having to right click - explore.

---

### Post by tamas305 on 2009-04-20
You could partition the drive with a fat32 partition that windows reads seperately from the partition where Ubuntu is installed with gParted. However I am not completely sure that will work with the live USB, it works with a full install.

Want a full install? Check this [thread]("http://ubuntuforums.org/showthread.php?t=1116206").
-tamas

---

### Post by mathspeedy on 2009-04-23
```
Tamas305 said:
You could partition the drive with a fat32 partition that windows reads seperately from the partition where Ubuntu is installed with gParted. However I am not completely sure that will work with the live USB, it works with a full install.

Want a full install? Check this [thread]("http://ubuntuforums.org/showthread.php?t=1116206").
-tamas     
```It is working, you just create 2 partitions[fat32]; one with the boot label and you just use the  System->Administration->Create a USB Startup Disk app. select the boot labeled partition and you have it done ...:biggrin:

---

### Post by C.S.Cameron on 2009-04-23
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

I find a preferable method is to disable the internal hard drives and install Ubuntu to the flash drive as if it was a regular hard drive.
When I get to partitioning I select manual then leave a FAT32 partition to the left for sharing with Windows, to the right of this I create a ext3 or ext4 partition and label it "/", then to the right of this another ext3 partition and label it "/home". You can leave a bit of swap space next to this but I'm not sure it is much use.
The drive is not as compact as using a disk image type install but is more flexible and can be updated and upgraded just like the real thing.

With a disk image persistent install using Unetbootin or usb-creator, you can save stuff to the disk from Windows as long as you do not use all of the space up for your persistence. To access the stuff while booted up in Ubuntu, you need to look in filesystem / cdrom.

---

