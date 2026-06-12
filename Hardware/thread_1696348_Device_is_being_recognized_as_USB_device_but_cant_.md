---
title: "Device is being recognized as USB device but cant mount storage"
date: 2011-02-27
forum: Hardware
---

### Post by roberj13 on 2011-02-27
I am trying to mount the internal storage on a Motorola Xoom. The storage mounts just fine in Windows7 but I don't want to have to use my wife's computer everytime I want to transfer a file. When I plug in the device there is a change in state on the device, but Ubuntu does nothing. 

I used lsusb and I see:

roberj13@rob-ubuntu:~$ lsusb
**Bus 002 Device 007: ID 22b8:70a9 Motorola PCS** 
Bus 002 Device 003: ID 064e:a127 Suyin Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:231d Hewlett-Packard 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


But fdisk shows nothing...


roberj13@rob-ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000667e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1959    15728640   83  Linux
/dev/sda2            3917       38914   281111553    5  Extended
/dev/sda3            1959        3917    15728640   83  Linux
/dev/sda5            3917        8379    35840000   83  Linux
/dev/sda6            8379       12841    35840000   83  Linux
/dev/sda7           12841       36364   188949504   83  Linux
/dev/sda8           36364       37639    10240000   82  Linux swap / Solaris
/dev/sda9           37639       38914    10237952   82  Linux swap / Solaris


dmesg | tail shows:

roberj13@rob-ubuntu:~$ dmesg | tail
[ 4572.808201] possible SYN flooding on port 57676. Sending cookies.
[ 4771.575947] usb 2-1.1: reset high speed USB device using ehci_hcd and address 7
[ 4772.464476] EXT4-fs (sda5): recovery complete
[ 4772.464681] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[ 4796.068163] npviewer.bin[3004]: segfault at 418 ip 00000000f6040d16 sp 00000000ff818cb8 error 6 in libflashplayer.so[f5dd3000+b5f000]
[ 5126.288362] lo: Disabled Privacy Extensions
[ 5832.150104] lo: Disabled Privacy Extensions
[ 6051.158397] Initializing USB Mass Storage driver...
[ 6051.158525] usbcore: registered new interface driver usb-storage
[ 6051.158529] USB Mass Storage support registered.


If anyone has any ideas on how to get this to work it would be appreciated. 

Thanks.

---

### Post by fjgaude on 2011-02-27
Maybe your Linux computer doesn't have NTFS-3g installed? What version of Ubuntu is there?

---

### Post by roberj13 on 2011-02-27
Thanks for the reply sorry about not putting what I have running. It is Ubuntu 10.10 x64. I don't know what else would be relevant since I know the hardware works, it mounts my phone's internal storage and SDCard storage just fine though, if that helps narrow it down.

---

### Post by fjgaude on 2011-02-27
I was totally off-base with the NTFS comment. Your machine is an Android so it is Linux to begin with.

The USB2 connection must be something special, not like a flash drive else fdisk would show it as /dev/sdb1 or /dev/sdc1.

Hopefully someone else has a suggestion, I can't think of what to try next, sorry!

---

### Post by fjgaude on 2011-02-27
Just thought of something: try mounting in the blind.

```
sudo mount -a

```

If you get a msg that states no mount point, then create one in /media.

If you don't know how to do that, ask for help.

---

### Post by roberj13 on 2011-02-27
sudo mount -a didn't do anything as far as I can tell. It is worth mentioning also to anyone else trying to help that even in Windows 7 the way the tab lists is completely different than my Android phone. When I mount my phone in Windows 7 it lists basically like a removable drive. The Xoom lists as a "mobile device" that windows accesses, but not really as a removable drive really. I remember a mp3 player I had listed this way as well a while back.

---

### Post by fjgaude on 2011-02-27
Okay, since we have something out of the ordinary, try installing System Profiler and Benchmark from the Ubuntu Software Center. It will show in Applications/System Tools after install.

Run it and see what shows at USB Devices and at Storage. This might give some idea what Ubuntu is up to.

---

### Post by roberj13 on 2011-02-27
[http://droid-themes.com/Downloads/hardinfo_report.html]("http://droid-themes.com/Downloads/hardinfo_report.html")

Here is the output of the System Profiler and Benchmark. The mounted drives are basically my root fs and home/ I don't really know why it's listing as sda5 and 6. But no USB devices are listed for some reason at all.

---

### Post by roberj13 on 2011-02-27
Also, while I was looking around I decided to check if the Android Debug Bridge works as expected. 

adb devices lists Android devices attached to the computer.


roberj13@rob-ubuntu:~$ adb devices
List of devices attached 
02783206435fc557	device

It also lets me shell into the device and actually access the storage. 

I can push and pull files from the storage with ADB but still Ubuntu still doesn't recognize what it's trying to be.

---

### Post by fjgaude on 2011-02-27
Okay, and thanks for showing the full report. When I put a USB drive into my machine it shows on the Storage section of the report. No USB drives shows in USB Devices.

Did you have a CD to install in Windows to get your wife's machine to show the drive in Xoom?

---

### Post by fjgaude on 2011-02-27
I have no way to install **adb**... where did it come from?

---

### Post by roberj13 on 2011-02-27
No there wasn't a CD. I had to install Motorola USB drivers from Moto's site then hooked up the Xoom and it installed whatever it needed and was up and running. I can actually push files to the storage through ADB but it's just a pain because it doesn't show progress but that may be my only option for right now anyways.

Now one thing I have found is that Linux users aren't the only one being affected by the odd USB implementation. Mac users have to download this app here. 

[http://www.android.com/filetransfer/](http://www.android.com/filetransfer/)

For some of the similarities between Mac OS this might be the same reason. 

I also checked back on the Windows machine and when the Xoom is connected it doesn't show up as a drive with a letter like most USB mass storage devices. So that may be whats confusing Buntu as well. 

It may be more worth my time to just get it working on VBox..lol

---

### Post by roberj13 on 2011-02-27
Actually I answered part of the question in my last post. Apparently the Xoom was supposed to be enabled to connect via MTP (which from what I read is a transfer protocol meant for mp3 and other media devices (zune) to talk to WMP etc directly) OR USB Mass Storage. Apparently the USB mass storage side of things is not working correctly ATM and it only wants to connect as an MTP device. That's why its not seeing it as a USB Mass Storage. So if I can make Ubuntu see MTP devices then I might be OK. So Google here I come. I will post findings so if anyone else comes looking they will be able to solve this as well.

---

### Post by fjgaude on 2011-02-27
Yes, VBox with Windows guest is usually a good option for things that don't work on Linux. Good luck!

---

### Post by roberj13 on 2011-02-27
So my temporary solution that I don't like but is better than loading up virtualbox everytime I want to move a file was this:

sudo apt-get install mtp-tools gmtp

gmtp is a gui that accesses mtp devices and will move and pull and files from the device. Not exactly as nice as just being able to use Nautilus but should just be a temporary fix to hopefully a temporary problem because UMS should work.

---

### Post by roberj13 on 2011-02-27
And....thanks for your help fjgaude. I would have given up a long time ago if you hadn't responded..lol

---

### Post by fjgaude on 2011-02-28
Glad you have at least a work around, a fix.

The world is moving so fast with so much media stuff and protocols coming out it will take more time for Linux to settle in with them all.

It would seem that Xoom would have a way to declare the USB as data storage so it appears as a flash drive or something like that.

---

### Post by bartman2589 on 2011-02-28
You might try installing the package mtpfs (available in the 'universe' repository for Maverick), it's a fuse filesystem driver that supports MTP devices, unless I'm mistaken it should let you access the device from nautilus and many other filemanagers, I don't have any MTP devices myself to test it with so I'm not sure if that will do the trick or not.  Hope this helps

---

### Post by fjgaude on 2011-02-28
Yes, yes! From info pages:

MTPfs is a FUSE filesystem that supports reading and writing from MTP (Media Transfer Protocol) devices, such as MP3 players, video players or digital cameras.

In addition to revealing media files on the connected device, MTPfs exposes a virtual directory called "/Playlists" which contains the device's playlists as m3u files.

Thank you, bartman!

---

### Post by bartman2589 on 2011-02-28
Glad I could help, now I just hope someone can help me with my 2 problems:

[http://ubuntuforums.org/showthread.php?p=10499331#post10499331](http://ubuntuforums.org/showthread.php?p=10499331#post10499331)

&

[http://ubuntuforums.org/showthread.php?p=10506706#post10506706](http://ubuntuforums.org/showthread.php?p=10506706#post10506706)

Have fun.

---

### Post by fishexe on 2011-06-24
It is correct that the main thing you need is mtpfs.  All the other posts about trying to find the right /dev/sdXX device are wrong.  I found complete instructions here: [http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html]("http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html").  I had to leave "USB debugging" unset on my tablet (contrary to the instructions) in order for it to work.  Hope that helps.

---

