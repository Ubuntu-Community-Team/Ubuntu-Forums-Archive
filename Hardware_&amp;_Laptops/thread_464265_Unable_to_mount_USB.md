---
title: "Unable to mount USB"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by Folk Theory on 2007-06-04
I just installed ubuntu Feisty Fawn and since it cannot recognize my wireless card i need to install ndiswrapper through  a USB flash drive to be able to connect to the internet. so i plug in the USB and it doesn't recognize it. i click on open and it says "unable to mount media. this probably doesn't contain any media" or some message very similar to this one.

i tried a different flash drive and tried many usb ports but to no avail. please help me, i am new to linux/ubuntu and i don't know whats wrong or how to fix it.

Folk Theory

---

### Post by slashdot87 on 2007-06-04
How old is your machine?  I installed Feisty Fawn on an older AMD Duron 1.0 Machine and have not had any problems with USB flash drives or whatnot.  I do not have a wireless card for this machine I am talking about, so I have not experienced issues in that area...

---

### Post by Folk Theory on 2007-06-04
its a Dell Inspiron 8100. couple of years though not TOO old. its a pentium 3.

---

### Post by slashdot87 on 2007-06-04
[http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/](http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/)


I found this using google.  I am not sure how much help it will be,but...



To manually mount a USB disk or USB drive or USB device in Linux or UNIX:

   1. Login as root. You can use the su command to switch to root user.
   2. Create a folder /mnt/USB with the command: mkdir /mnt/USB
   3. Add the following line in the file /etc/fstab (fstab is the file that tells Linux where to mount the various devices, and thus simplying the mount command):

      /dev/sda1 /mnt/USB auto noauto,owner,kuzu 0 0

      Note: The “auto” on the above line means auto detection of filesystem. If your system unable to determine the filesystem type, change it accordingly to the USB drive’s filesystem (e.g. vfat or ntfs or ext2 or ext3).
   4. Mount the USB storage device with the following command: mount /dev/sda1

Without the need modifying fstab (step 3), you can also straight away issue the mount command (step 4) with the following syntax:

mount /dev/sda1 /mnt/USB

If you know the filesystem of the USB drive or the system unable to determine the correct filesystem, the -t option can be used to the filesystem type of the USB device:

mount -t vfat /dev/sda1 /mnt/usb (for vFAT filesystem)
mount -t ntfs /dev/sda1 /mnt/usb (for NTFS filesystem)

Sometimes, the USB drive or USB storage device is detected by the system but been assigned a different device name from sda1. If so, the correct device name need to be determined by viewing and OS log file. Usually the Linux and UNIX boot and log message is stored in /var/log/messages, and you can view the log messages with the following commands:

tail -f /var/log/messages

or

dmesg

Check for the name of the device that appears after operating system detects the USB devices.

After using the USB disk, remember to unmount the USB drive with the following command to avoid any possible loss to the data or changes and risk messing up your partition.

umount /mnt/USB

Configure Gnome to automatically detect, install and mount USB drive

If you’re using Gnome yet unable to automatically detect and mount USB drive for usage, a few packages needed to be install. The packages to install are dbus, hald and Gnome-Volume-Manager. After installing these packages, configure dbus and hald setup to run via init scripts. Then in Gnome, some configuration has to be done. Click on the ‘Desktop’ menu, then go to ‘Preferences’, and then to ‘Removable Drives and Media’. Configure the settings to your liking. Once you plug-in a usb drive, an icon for the drive will appear on the desktop. Other possible setting is to have Gnome opens a window showing the contents of the USB drive.

---

