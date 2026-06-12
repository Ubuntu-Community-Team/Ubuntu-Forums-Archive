---
title: "How to update motherboard BIOS from USB drive"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by jac1d on 2007-06-26
Upgrade your motherboard BIOS firmware from a USB thumb drive
How to make a USB memory key in to a bootable DOS drive
By: Jeff Campbell, Turks & Caicos Islands, British West Indies
June 25, 2007


It happens all the time, you have a newish machine that lacks a floppy drive, and you have a need to either upgrade the BIOS from DOS or run some other esoteric application that can only be done from DOS – the problem is, with no floppy drive (and god only knows where your last set of DOS boot disks went) and only Windows XP on hand, how can you create a bootable DOS environment?

Well if you have two optical drives, it's easy.  You can simply download the FreeDOS LiveCD (base image) from [http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso) and burn that to a CD.  You can then burn the BIOS flashing utility and the BIOS image from your motherboard website to another disc, boot up your box, change to the second drive, and run the utility

But what if you don't have two optical drives?  Or what if you don't have ANY optical drives?  I found myself in this situation recently.  I was working on an appliance that had only a compact flash (CF) boot slot, and a few USB ports.  It lacked not only an optical drive but also a hard drive, and I needed to flash the BIOS to current.

I did the usual Googling and found lots of outdated articles, none of which adequately explained how to make a USB key boot DOS, although I did piece together enough clues to figure it out with some experimentation.

You'll need a few things to make a DOS bootable USB thumbdrive with these instructions:

The HP Flash Drive Format Utility (via the PC World Website):
[http://www.pcworld.com/downloads/file/fid,64963-page,1-c,downloads/description.html](http://www.pcworld.com/downloads/file/fid,64963-page,1-c,downloads/description.html)

The FreeDOS 1.0 base image ISO:
[http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso) 

The WinImage Utility:
[http://america.winimage.com/download/winima80.exe](http://america.winimage.com/download/winima80.exe)


Steps to make your fancy, schmancy DOS booting USB drive:

1.Download and install the HP USB Disk Storage Format Tool and WinImage

2.Make a directory on your desktop called “DOSBootDisk”

3.Start WinImage and open the fdbasecd.iso file, you will see a directory structure
a.Select Image > Extract and browse to your DOSBootDisk directory
b.Check the “Extract all files into the same folder” and click “OK”
c.When it prompts you if you want to overwrite duplicates, say Yes
d.You can now exit WinImage, you won't need it again

4.Connect your USB flash drive to your machine and backup any files you want to keep (as it will be completely erased in this process)

5.Start the HP Flash Format utility
a.In the first dropdown box, select your flash drive (mine displays as a Corsair 2GB flash drive).  Be careful that you have the correct drive as this process will erase your device.
b.Set the File System to FAT
c.If you want, give your system a volume label, for example “BOOTDISK”
d.Check the “Create a DOS startup disk” box
e.Select “Using DOS system files located at:” and browse to your desktop and select your DOSBootDisk you created in step 2.
f.Click Start and say Yes when it warns you about formatting your device
g.Watch the pretty status bar progress
h.Click “Close” when it is done

6.Now open your formatted USB key in Windows Explorer and copy your BIOS flash utility and your BIOS image to your key so they are available once you reboot.  Feel free to throw in any other DOS utilities you want... I can't think of any but since you're here you obviously know something about DOS...

7.Shut down Windows XP, reboot your machine, ensure your BIOS is set to support booting from a USB device (this varies by BIOS, ensure both the option is enabled and your USB device is in your boot order about your hard drive and optical drive).  Save your changes and exit.

8.You should see your machine boot FreeDOS 1.0 from your USB key.

9.Run the BIOS upgrade utilities you copied to the disk earlier.

-Jeff

---

### Post by tcoffeep on 2007-06-26
How do you know which BIOS flash utility is the one for your BIOS?

---

### Post by CrispyFried on 2007-06-26
check the manufacturer web site, they will tell you.

---

### Post by ramjet_1953 on 2007-06-26
Updating your BIOS at the best of times is a very risky business.

You should NEVER flash your BIOS, just because you want the "Latest and Greatest".

Why? Simply because if something goes wrong during the flash, you will have a dead motherboard!

Certainly, if your motherboard has a Dual-BIOS setup, you can always fall-back on the previous version, but not many have this feature.

The ONLY reson to re-flash a BIOS is if there is a problem that you have that can only be addressed by upgrading.

The golden rule here is "If it isn't broken, don't try to fix it"

Regards,
Roger :cool:

---

### Post by talen.quickblade on 2008-02-26
A how to for those of us who are windows deficient would be nice as well... Anyone?

---

### Post by ufomekaniker on 2008-05-06
Is it me, or is it pretty odd that the BIOS update solutions shown here does not use Linux at all. Even Windows has been mentioned. Does there even exist an Ubuntu BIOS update tool? Or even an USB update tool made from within Ubuntu?

I've looked alot on Google, and followed alot of the Google-fans links. But nothing really works, and many of the pages has dead links. 

Whats wrong with right click on the USB ikon and choose make boot USBdrive?

I need to Update my BIOS because it's not ACPI compliant, and therefore all my harddrives are warming ALOT in my server, and i also need to save energy too. It's an VIA Epia EN15000 motherboard.

---

