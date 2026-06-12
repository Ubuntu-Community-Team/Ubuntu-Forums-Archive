---
title: "Help with mounting to USB"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by spect3r on 2009-11-09
Hi everyone, 

I want to install the netbook remix on a toshiba nb200 (no cd drive), so I need to write the iso to a thumbdrive. I am doing the mount in windows. 

I downloaded virtual clone drive and mounted the ubuntu iso to a virtual drive (J:)

The thumbdrive is formatted 4GB FAT32. 

When I run the usb-creator.exe included in the ubuntu cd/iso, I get the following error: 

*An uncaught exception was raised: [Errno 13] Permission Denied. *

I have tried to follow the tutorial [here]("https://help.ubuntu.com/community/Installation/FromUSBStick#Prepare the USB Drive"), but I get stuck on the above... 

Any idea/help? Thanks!

---

### Post by teward on 2009-11-09
are you running the image burn as an administrator on the Windows computer?

---

### Post by spect3r on 2009-11-09
> **TrekCaptainUSA said:**
> are you running the image burn as an administrator on the Windows computer?

You bet.. on both virtual clone and usb-creator... (right click runas/administrator)

---

### Post by darkod on 2009-11-09
usb-creator from the netbook remix image of 9.10 didn't work for me anyway. Not on Vista and not on 7. Even running as admin didn't help, the Make button is grayed out.

Another easy way to create bootable USB stick with ubuntu is:
1. Go on google and find and download unetbootin software. It's free.
2. Run the software and it will let you select ISO option, then select the remix image.
3. In the list of available USB thumb drives, select the correct one.
4. Click on Ok and you're done. At the end do not select reboot, just exit the program.

Now, if you want the original ubuntu menu present at start, open the USB drive and do the following:
1. In the root, rename the syslinux.cfg file to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

The USB stick will boot up into the standard ubuntu menu, first option Try Ubuntu, second Install Ubuntu, etc

PS. All of the above is done in windows of course.

---

### Post by spect3r on 2009-11-09
Holy crap! Talk about quick replies.. thanks guys. I will try your solution and let you know how it goes! ;)

---

### Post by spect3r on 2009-11-09
Yes, darkod, that worked. Thank you!!! 

Mark as solved :)

---

### Post by darkod on 2009-11-09
No problem. Glad I could help.

I forgot to mention earlier but if I were you (or the user of the netbook), I would choose the option Try Ubuntu first. To see if it will work and whether you like it.

Then I would also download the desktop 32bit image and use unetbootin to put it on the USB stick (after formatting it). Then try how you like the regular desktop version.

There is a difference in the layout and it's up to personal preference.

I installed remix without checking how desktop looks like, and didn't like it. So after I had to install desktop again over it. :)

The desktop version works just fine on a netbook too.

---

### Post by leorolla on 2009-11-10
> **darkod said:**
> usb-creator from the netbook remix image of 9.10 didn't work for me anyway. Not on Vista and not on 7. Even running as admin didn't help, the Make button is grayed out.

Another easy way to create bootable USB stick with ubuntu is:
1. Go on google and find and download unetbootin software. It's free.
2. Run the software and it will let you select ISO option, then select the remix image.
3. In the list of available USB thumb drives, select the correct one.
4. Click on Ok and you're done. At the end do not select reboot, just exit the program.

Now, if you want the original ubuntu menu present at start, open the USB drive and do the following:
1. In the root, rename the syslinux.cfg file to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

The USB stick will boot up into the standard ubuntu menu, first option Try Ubuntu, second Install Ubuntu, etc

PS. All of the above is done in windows of course.

Thanks for the hints!

Do you know a *general* tool for making a Live USB (or a live partition of a USB) from any ISO file, so that the USB behaves "as if" it were the CD, besides Unetbootin+tweaks?

---

### Post by wilee-nilee on 2009-11-10
> **leorolla said:**
> Thanks for the hints!

Do you know a *general* tool for making a Live USB (or a live partition of a USB) from any ISO file, so that the USB behaves "as if" it were the CD, besides Unetbootin+tweaks?

You might want to start your own thread on this, I suspect there isn't a load any ISO to USB tool, I was unable to get the USB creator in UBUNTU to put Puppy Linux on a USB.

---

### Post by leorolla on 2009-11-10
Hi Darkod,

In

1. In the root, rename the syslinux.cfg file to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux


Did you miss

4. Move syslinux.cfg from syslinux/ to the root

?

I did that with gParted and it worked flawlessly.

---

