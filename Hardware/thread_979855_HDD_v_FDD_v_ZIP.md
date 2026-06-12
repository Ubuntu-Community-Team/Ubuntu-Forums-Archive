---
title: "HDD v FDD v ZIP"
date: 2008-11-12
forum: Hardware
---

### Post by Rplus9 on 2008-11-12
I am having trouble finding a clear answer to this question.  I'm trying to ditch burning a new CD every time I want to change linux etc... and I bought a USB 1G drive for just that purpose.

Now my bios is either odd, or just old enough to support:
USB-FDD
USB-ZIP

but not
USB-HDD

so obviously, my USB-HDD (I'm assuming that's what it is) won't boot.  I have an older 500MB usb drive that will boot, so it seems to be something specific to the 1GB drive.

Could someone explain to me the differences (FDD-ZIP-HDD) is it a hardware specific thing?  can it be changed? if so, how?

Thanks!

---

### Post by Rplus9 on 2008-11-12
what a tick... if FDD floppy disk drive...

Why are some of my USB drives FDD, ZIP or HDD?

still can't find clear instructions on how to make that happen.

---

### Post by jerome1232 on 2008-11-12
This kind of thing is very bios independent. 

For example on this computer, usb drives get treated as normal HDD's (Hard Disk Drives) and I just have to change the order to boot drives in my bios. 

Do you know what type of bios it is? (All of mine are phoenix award flash bios).

On my other computer If it picks up a usb drive the bios will actually prompt me if I would like it to be selected as the boot device.

I'm afraid your going to have to fish around in you bios to figure this one out, if it can boot off of usb floppy drives and usb zip drives it should boot off of usb hard disk drives

---

### Post by Rplus9 on 2008-11-12
[http://www.pendrivelinux.com/2007/02/20/booting-linux-from-usb-zip-on-older-systems/](http://www.pendrivelinux.com/2007/02/20/booting-linux-from-usb-zip-on-older-systems/)

going to try this when I get home.

so answering my own question the difference is the device on the other end of the USB device,

apparently you can mimic other devices on a technically USB-HDD
it's not too bad but be careful you might really hose things if you do it wrong.

I'm concerned that I'll be limiting the device size, but I guess I'll see.

The Process:

   1. Insert your USB Flash drive
   2. Open a terminal window and type sudo su
   3. Type apt-get install syslinux (if you don't have syslinux installed)
   4. Type apt-get install mtools (if you don't have mtools installed)
   5. Type fdisk -l to list the available disks (make note of your flash drive from the list)
   6. Type mkdiskimage -4 /dev/sdx 0 64 32 (replacing x with your actual flash drive letter)
   7. After the process has completed (takes a while) type fdisk -l and confirm the new geometry of the flash drive "64 heads, 32 sectors"
   8. Type syslinux /dev/sdx4 (replace x with your flash drive letter) to make the drive Linux bootable

---

### Post by DrMelon on 2008-11-12
I found that eventually the only thing that worked for me was this:
The PLoP Bootmanager. It allows booting from USB devices if your BIOS doesn't support it; in this case, your problem was exactly the same as mine!

[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

Can be used with hard drive, NTLDR, floppy, cd, whatever you want the bootloader to be on.

---

### Post by Rplus9 on 2008-11-13
Well, I got it working.

My hardware is just old enough to NOT support USB-HDD, but it will support USB-ZIP (and USB-FDD).

So I followed the instructions (listed above) and was able to, I guess spoof, a USB-ZIP "structure" on my USB-HDD (1GB thumb drive)

It worked wonderfully well, it even "fixed" another issue I had with Linux Mint install not seeing my hard-disks. 

So now I'll be CD free with every new install.

Oh I also recommend UNetbootin, makes the final formatting a breeze.  You can even do it from the disks but I've had some limited success with that.

Now I am curious about this PLoP, I've got an old laptop without a CD-rom (thing died) I was able to recover it by stealing another drive (oddly not all are compatible)  But then I've done my installs using the "/" option on UNetbootin.  However I'd prefer to use USB.  I can't get to that website from work so I'll have to check it out at home.

---

