---
title: "Camera Won't Show Up in Devices"
date: 2014-05-10
forum: Hardware
---

### Post by HDTimeshifter on 2014-05-10
When I plug in my camera via a USB port, it won't show up under the devices in the file manager. I tried toggling my System Settings / Details / Removable Media / Photos to "Ask What to Do" and "Open Folder". I tried unplugging and replugging in the USB cord (both ends - PC and camera) and restarting the PC. I noticed that my SD card was blank, so took a picture and the camera still won't show up under the devices, so I have no way to access it to copy or delete photos from it. The camera is getting power from the USB as it does charge when plugged in. I'm running 14.04 LTS.

---

### Post by gordintoronto on 2014-05-10
What camera? The procedure I use is to plug in the camera, then turn it on, and up it pops.

Can you open a terminal window and enter this command: lsusb

Then paste the output back here.

---

### Post by HDTimeshifter on 2014-05-11
The Olympus camera LCD turns on and shows charging as soon as I plug it in. It shows up in lsub, but not under the devices in the Files application like it used to.

> Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07b4:012b Olympus Optical Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by HDTimeshifter on 2014-05-17
I tried inserting my memory card into a SanDisk card reader and plugged it into a USB port and it doesn't show up in the Files application left tab either even though its LED lights up. This is the lsub output (I tried multiple USB ports including one on the rear next to my mouse, keyboard, and printer to eliminate the possibility of a bad port) so the camera isn't the problem:
> Bus 001 Device 002: ID 0781:9393 SanDisk Corp. ImageMate SD-MMC
Bus 001 Device 003: ID 0781:9393 SanDisk Corp. ImageMate SD-MMC
Bus 002 Device 004: ID 0781:9393 SanDisk Corp. ImageMate SD-MMC


I'll try booting into Windows and see if it can see the devices.

---

### Post by HDTimeshifter on 2014-07-06
Bueller? Nobody else has this issue? It's either a bug with Ubuntu or its File Manager.

I just plugged my Android into a USB port and while the phone displays "USB connected", it does not show up in the File Manager Devices either.

I was able to see my camera in Windows 7 and download them onto my Windows drive, however, since Windows can't see my Linux drive and Ubuntu can see Windows drives, I usually copy files from my Linux drive to Windows drive for backup and forgot to copy the photos from my Windows drive to my Linux drive and ended up wiping out the photos when I copied Linux to Windows! I had already deleted the SD card to make space for more photos too! Photos lost forever! Any solution? I'd hate to loose more photos because of this and it's a pain to have to boot to Windows (and spend hours waiting for it to update) since I spend 99.99% of the time running Ubuntu!

---

### Post by xc3RnbFO8P on 2014-07-06
We can try
install PWC in Ubuntu Software Center and restart
do **dmesg** in Terminal and see if the camera is spotted

---

### Post by ibjsb4 on 2014-07-06
This any help?

[http://ubuntuforums.org/showthread.php?t=2229673&p=13051335&viewfull=1#post13051335](http://ubuntuforums.org/showthread.php?t=2229673&p=13051335&viewfull=1#post13051335)

---

### Post by HDTimeshifter on 2014-07-06
Hmm, I booted into Win7 and downloaded photos from my phone, then camera, but when I closed out the Explorer windows and camera app windows, there was no icon in the bottom area to disconnect the camera USB safely (and none in Explorer for the camera device), so I rebooted without disconnecting and when Ubuntu booted up, the camera shows up in the File Devices. I clicked on the eject icon, then replugged in the camera and it shows up again. I then plugged in my phone, and a File window comes up and am able to browse the SD card. I think the problem may be related to after the computer resumes from sleep - I'll try plugging in my devices next time the computer resumes from sleep and see if USB hot plug and play works then. I used to have a problem with my networking not re-enabling after resume until I put something in a file to reload the driver upon resume.

Ringi, I'll try installing PWC later and report on the results.
ibjsb4, if PWC doesn't work, I'll try installing Shotwell.
Thanks guys.

---

