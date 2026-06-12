---
title: "Startup Disk Creator Formats All Connected Drives"
date: 2010-11-22
forum: Hardware
---

### Post by Dipper on 2010-11-22
I was attempting to create a bootable USB image of Ubuntu 10.10.  I am currently using 10.04.  Connected to my computer were the 8 GB SanDisk USB stick, a DVD burner, and a 320 GB external hard drive.  

When I selected the 8 GB stick for formatting, I made sure NOT to format the 320 GB drive, since that is where all of my pictures, music, basically my whole life is located.  Once I triple checked to make sure the correct device was to be formatted, I created the USB startup device.

When I opened the 320 GB drive, I found that instead of all my data, it contained basic linux folders (bin, boot, home, etc, lib, and so on).  All of my stuff appears to be gone.  When I looked at the properties of the drive, the graphic says that 17.0 GB is used, but yet it calculates 1.8 GB of data when viewing the properties.

The drive was originally formatted as a FAT 32, but now shows as ext3/ext4.  Is there any way to access the most important things on that drive.  It is as if my house burned down in less than 2 minutes.

Please help.

---

### Post by wet-willy on 2010-11-23
Well...
When startup disk creator creates a live USB, (bootable USB image of Ubuntu 10.10.), it formats FAT32. Obviously you chose to install to the computer rather than create a live USB as your 320 is formatted ext3 and there appears to be a hard drive install rather than a CD image.

Burn the Ubuntu iso to disk and boot it up, update your repositories and install testdisk. Once installed, open a terminal maximized and run command: **fdisk -l** while the 320 is tethered to see which device it is, (just a note of advice: if you don't need the Sandisk at this point, unplug it). Now issue command: **photorec** , use arrow, space bar and return key to navigate the steps and select the appropriate drive/and or partition to recover from/to, and the type of files to look for. You'll be required to have another partition or drive to send recovered files to, you may need another 320GB, or you can stop/resume photorec to give time to go through recovered files to delete what you don't need if space is limited. The man pages aught to explain further.

---

