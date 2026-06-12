---
title: "Success with an HP Pavilion ze2308wm"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by Greg2 on 2006-01-04
I wasn't sure where to post this, but Laptop Support seemed to be the appropriate place.

I have been reading the forums here since November 05, so I will start by saying hello because this is my first post. So hello and thanks to everyone here for a great forum.

This is about a very easy and successful Dual boot install of Ubuntu Breezy Badger 5.10 on an HP Pavilion ze2308wm laptop aka “Walmart BF '05 Laptop”.
Laptop specs:
[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00521954&lc=en](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00521954&lc=en)

After my 'very early morning' Walmart Black Friday laptop purchase at $378 USD, I proceeded to Staples for a Black Friday purchase of  PNY 512MB PC2700 DDR notebook memory for $39 USD (after $20 rebate). I took these items home with a smile on my face and the hope that I could install Ubuntu Linux on my 'first' laptop.

This is what I have done to my laptop:

1st-  Move the original 256MB from the first slot to the second, then install new 512MB chip in the first slot. Enter bios and set video memory to 64MB, this left me with 704MB of system memory.

2nd- Format the hard drive with the Windows recovery disk and just install the needed system files, programs and drivers for my needs with windows. This step gave me over 3.5GB more of hard disk space and increased performance by.... will that's a windoze thing.

3rd- Resize the Windows NTFS partition with qtparted using the 'System Rescue CD' as described here:
[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)
Then remove the System Rescue CD and insert the Ubuntu installation CD and reboot the system and install Ubuntu into the free space, as per the same how-to. For the record I partitioned my hard drive like this:
/dev/hda1 ntfs  15.1GB for windows
/dev/hda2 ext3   7.1GB for /
/dev/hda3 linux swap 972MB
/dev/hda4 ext3  15.1GB for /home

and installed grub to the mbr without any problems.

  *see Dapper Drake note at end of post *
 
4th- The first boot was enabled by typing when prompted:
```
linux vga=771
```
Then to get X working, the battery indicator, Ati Radeon Xpress 200 and the Broadcom wifi card I found help in this thread:
[http://www.ubuntuforums.org/showthread.php?t=100924&highlight=ATI+Radeon+Xpress+200](http://www.ubuntuforums.org/showthread.php?t=100924&highlight=ATI+Radeon+Xpress+200)

Reboot in recovery mode and edit my xorg.conf with:
```
 sudo pico /etc/X11/xorg.conf
```
and in the device cell where Ati driver is called, edit by adding the line:
```
Option     “noaccel”
```
Then restart the gui with:
```
sudo /etc/init.d/gdm restart
```
The next thing was to use debernardis's kernel boot magic on the grub by editing the menu.1st file with the line:
```
acpi=strict acpi=noirq pci=biosirq pci=nosort irqpoll routeirq
```
Now I was up and running and reading the forum with my laptop. Thanks,  debernardis!

5th- Next I went to this HowTo:
[http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589](http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589)
Followed the instructions very carefully and here are the results:```

greg@halfway:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

greg@halfway:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
4213 frames in 5.0 seconds = 842.530 FPS
4259 frames in 5.0 seconds = 851.708 FPS
4260 frames in 5.0 seconds = 851.877 FPS
4258 frames in 5.0 seconds = 851.503 FPS
4258 frames in 5.0 seconds = 851.570 FPS
```
Thanks, mlomker!

6th- Now it was off to this HowTo for my Broadcom wifi card:
[http://ubuntuforums.org/showthread.php?t=104539](http://ubuntuforums.org/showthread.php?t=104539)
I followed the instructions and compiled new ndiswrapper and ndiswrapper-utils. Then I used dpkg to install the  ndiswrapper, ndiswrapper-utils and the ndisgtk. I use ndisgtk to install the drivers and it works very well.
Thanks, foxy123!

7th- Next was the modem, so I went to:
[http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
Installed the hsfmodem_7.18.00.07full_k2.6.12_9_386_ubuntu_i386.deb driver with dpkg. Configured my ppp0 and dialed out and connected to an isp. Please note that this was the free test version that is limited to 14.4Kbps... but it worked.

As of the time of this posting (with my new laptop using Ubuntu) I have found no problems with it's operation. The buttons all seem to work including wireless power, volume and mute, screen brightness, etc. Everything I have had to do is noted in this post. If I have any problems I will post them at a later date.

Thanks to everyone involved in this Great Linux Distro, and everyone that donates their time to help on this forum.

 *Edit: I now have Dapper Drake 6.06 installed on this laptop without any boot parameters.*

---

