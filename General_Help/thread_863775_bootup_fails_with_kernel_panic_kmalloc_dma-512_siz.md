---
title: "bootup fails with kernel panic kmalloc_dma-512 size=512 failed."
date: 2008-07-18
forum: General Help
---

### Post by Blonddeeni on 2008-07-18
Gidday. 
Occasionally my system fails to load; showing these four lines on the display. (I've removed the splash screen option from the grub menu).

Starting Up...
Loading please wait...
[  6.142000] Kobject_add failed for :d-0000512 with -EEXIST,  don't try to register things with the same name in the same directory.
[  6.142000] Kernel panic - not syncing: Creation of kmalloc slab kmalloc_dma-512 size=512 failed.

Interestingly, the 6.1420000 number does not appear anywhere in the kern.log or the syslog for any of the boot sequences in the past.
Also, this can occur twice in a week, or not at all for a month.
The only way to get in is to do a manual reboot using the reset button, as the keyboard is locked out. Not even the 'caps-lock' key works.
This error message occurs regardless of whether it is a manual boot-up, or an automatic boot-up from the onboard ACPI timer.

here are the spec's of my system.
Motherboard:	 Asus M2NPV-VM
CPU:             AMD64 Athlon X2 5200+
Memory:		 DDR800 1G
Hard Drives x 2:  Seagate Sata 500G  with two 400G partitions  that have been LVM'd together.
Mouse:		 Microsoft PS2
Keyboard:		 Genius PS2 (Have just tried another Make of PS2, same problem)

Display : I switch between Philips lcd and my TV which uses AV. (Currently unable to use both at the same time, so have to reboot and change plugs to  change display, which is very awkward).

USB Dongle for the Mythtv remote receiver: (input: USB HID v1.10 Keyboard [Formosa21 USB IR Receiver] on usb-0000:00:0b.0-2)
Two Skystar-2 DVB-S cards for receiving Freeview signals for Mythtv. 

OS: Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
ACPI

/usr/bin/mythbackend --version
Source code version     : Unknown
SVN branch              : trunk
Library API version     : 0.21.20080114-1
Network Protocol Version: 38
Options compiled in:
 linux debug using_oss using_alsa using_arts using_jack using_backend using_dbox2 using_dvb using_firewire using_frontend using_hdhomerun using_iptv using_ivtv using_joystick_menu using_lirc using_opengl_vsync using_opengl_video using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw using_bindings_perl using_opengl using_libavc_5_3 using_live

Internet via a dial-up modem, which max's out at 4KB/sec, but usually sits at around 2.5KB/s. So just a 1meg transfer can take up to an hour sometimes.
To build the system I had to uplift the entire assembly, move couple of hundred km's to a friend's house with faster interweb, and camp there for a few days.

I have looked at the kernal log and the syslog and have been unable to see any difference between a failed boot sequence and a successful boot.
But as I am a noobie at all this, well..... what am I looking for? (I just go to the end of the failed log sequence and compare the results).

Have looked around the forums (+ google) and can only discover three other instances of this fault:
1) Having a USB card plugged in at boot via a dongle for an external hard drive.
2) Having two sata drives plugged in with a LVM partition. No reference was made as to whether internal or external.
3) Having a Genius keyboard plugged in, but no reference was made as to PS2 or USB. ([http://ubuntuforums.org/archive/index.php/t-710451.html](http://ubuntuforums.org/archive/index.php/t-710451.html))

I've changed the keyboards, (but both were PS2), removed the USB IR receiver, but no luck.

My other idea is the hostname causing problems, (Grunta+). I'm not sure how the "+" got in there, but all attempts to remove it have prevented Mythtv from working correctly, or at all sometimes.

Any ideas for a Noobie anyone?
 
I can provide the kern.log and syslog if required, but as they are incredibly long, not sure if they would fit within the restraints of a message post.

Cheers
Blonddeeni.

---

