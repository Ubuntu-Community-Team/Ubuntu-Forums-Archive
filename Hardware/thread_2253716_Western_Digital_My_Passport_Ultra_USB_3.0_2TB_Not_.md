---
title: "Western Digital My Passport Ultra USB 3.0 2TB Not recgonized in Ubuntu 14.04"
date: 2014-11-21
forum: Hardware
---

### Post by dk_sn1p3r on 2014-11-21
I also have been having trouble with my Western Digital USb hard drive.  I have searched online quite a bit and have not found a way to get my device recgonized by my Ubuntu 14.04 Desktop nor my Xbuntu 1U Server.  Doing a ls USB returns nothing in the desktop.  I see three hard drives in the /dev/UUID folder and I'm guessing they are my IDE hard drive my DVD Rom and the USB drive.  I'm not sure what I should do to make the drive usable.  I've seen a thread similar about making ubuntu 14.04 persuadable to see the drive but I'm not sure what that process is.

*****EDIT: I just noticed in my bios when the drive is connected to the desktop it has two devices it lists in the USB mass storage device configuration section.  It has the WD My Passport and it also has WD SES Device.  I'm guessing that is the internal encryption section of the drive.I'm going to try and monkey with the options for both of those: auto, floppy, forced FDD, hard drive, CDROM, and see if changing them from auto fixes the issue in Ubuntu. ***** 

sudo lsusb detects: Western Digital Technologies, Inc.
the ubuntu disk application sees the drive too it just doesn't auto mount it.
The mount option for the drive is grayed out along with everything else except the power down option.  I've only tried using the device in usb 2.0 ports.
I tried enabling automount on startup and it hangs saying drive isn't ready.
The drive works perfectly fine on my windows 7 desktop and my windows 8.1.  All of my machines are x64 and have 64 bit software on them.  The drive is formatted in NTFS scan disk on windows comes back clean on it.  

This is so weird it just magically auto mounted.  Wierd, I wish I knew a definitive procedure to get this device to work consistently and a little faster?!?

Any help would be greatly appreciated!

Thanks in advance,

-Jon

---

### Post by Mark Phelps on 2014-11-22
Some WD Passport drives are set up so that, when you first use it (in Windows, of course), you are prompted to assign a password.  If you do that, WD then encrypts the drive, and after that, you have to provide a password to access it.  Did you do this?

Also, some of the WD Passport drives come configured with a front-end that only works in MS Windows -- which is why it will work OK in Win7 and Win8.1, but Linux distros can't mount the drive.

I've read that removing the assigned password then allows the drive to be mounted in Linux because it basically decrypts the drive.  But, I don't have such a drive, so I can't confirm that.

---

