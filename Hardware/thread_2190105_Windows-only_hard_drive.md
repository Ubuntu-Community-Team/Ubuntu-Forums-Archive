---
title: "Windows-only hard drive?"
date: 2013-11-25
forum: Hardware
---

### Post by Kelvari on 2013-11-25
I just saw the WD Black 2 Dual Drive (128GB SSD + 1TB HDD in one chassis) on [C|net](http://reviews.cnet.com/laptop-hard-drives/wd-black-2-dual/4505-9997_7-35832702.html?ttag=fbwp), and was wondering if anyone has managed to get their hands on one of these for use in Ubuntu. Not planning on putting it in my current laptop, but considering something similar for a future laptop.

---

### Post by Bucky Ball on 2013-11-26
You thread title says 'Window only hard drive'. Not aware there is such a thing. Are you actually wanting to know if the WD Black 2 Dual Drive will only work in Windows and not Ubuntu? I can't imagine that to be the case.

If you do some research (recommended before posting) you will see that people mainly have issues with the BIOS not recognising the drive rather than the operating system.

---

### Post by VMC on 2013-11-26
> **Kelvari said:**
> I just saw the WD Black 2 Dual Drive (128GB SSD + 1TB HDD in one chassis) on [C|net]("http://reviews.cnet.com/laptop-hard-drives/wd-black-2-dual/4505-9997_7-35832702.html?ttag=fbwp"), and was wondering if anyone has managed to get their hands on one of these for use in Ubuntu. Not planning on putting it in my current laptop, but considering something similar for a future laptop.
According to the comments on that C|net link, here is the reason why you can't use it in Linux/Mac:
> [dlauber]("http://www.cnet.com/profile/dlauber")[FONT=inherit]
[COLOR=#000000][FONT=inherit][FONT=inherit]I just viewed the excellent videos at Western Digital's site on cloning to this drive and fresh installations. My idea of first installing with Windows and then cloning an Apple drive to the SSD portion probably will NOT work. You've got to leave the WD software installed in order to access the 1 TB hard drive portion. Oh, well, it was a nice idea. This drive is already available at newegg.com.
[/FONT][/FONT][/COLOR][/FONT]
[@[FONT=inherit]dlauber[/FONT]]("http://www.cnet.com/profile/dlauber")[COLOR=#000000][FONT=inherit] The software installs the appropriate driver for Windows to interact with the newly-created partition, so unless Western Digital actually develops a way for OS X to do the same (this depends on how collaborative Apple might be with them) it won't be possible to use it on a Mac laptop. The time has come to see how much Apple cares for its customers.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2013-11-26
And this:

> To use the WD Black Dual Drive, users have to first set up the Windows (NASDAQ: MSFT) operating system on the SSD portion of the drive. Subsequently, a Windows-only software will have to be installed to unlock the HDD portion of the drive and format it for use. As such, other operating platforms including the Mac OS X (NASDAQ: AAPL) and Linux are not supported.

[http://www.fiercecio.com/techwatch/story/wd-black-dual-drive-combines-128gb-ssd-1tb-hdd/2013-11-26](http://www.fiercecio.com/techwatch/story/wd-black-dual-drive-combines-128gb-ssd-1tb-hdd/2013-11-26)

... and this:
> 
The drive supports operating systems ranging from Windows XP to Windows 8.1, but does not support Apple Mac OS or Linux.

[http://www.xbitlabs.com/news/storage/display/20131125212457_Western_Digital_Unleashes_WD_Black2_World_s_First_SSD_HDD_Dual_Drive.html](http://www.xbitlabs.com/news/storage/display/20131125212457_Western_Digital_Unleashes_WD_Black2_World_s_First_SSD_HDD_Dual_Drive.html)

Still can't figure out, though, if once it's set up using a Windows machine it might be usable. Guess they'd give instructions on how to do that if you could.

---

### Post by Mark Phelps on 2013-11-26
Some WD external drives use a Windows front end to encrypt the drive by default.  That's why the drive is considered "windows -only".

However, some folks have had luck accessing these drives if they first decrypt the drive and remove the password.

---

### Post by radu.c on 2014-04-15
I just encountered one of these. I haven't seen it from day one, but apparently it shows up as a 120 GB SSD when you take it out of the box. Then you install Windows on it as per usual - if you're into that sort of stuff, and even if you're not, as you don't actually have a choice in the matter here. Then you run the WD hocus pocus software that activates the HDD part of the device, reboot, and you have a weird partition that has id 7 but isn't NTFS that matches the HDD area of the device. The drive itself is now presented as a 1120 GB disk.

Once that is done, Ubuntu sees the full 1120 GB drive, so you can delete the Devil's Operating System and install Linux, but you need to be careful to not straddle the boundary. So, basically delete the Windows partitions (apparently there will be two, one for the bootloader) and install your Linux in the "available space" there. I'm yet to try to re-format the HDD partition as ext4, but I'll do that tomorrow and see how it goes. The main idea is to re-format the HDD partition and change its ID, but never delete and re-create it, because that will most likely not be aligned properly anymore.

My feeling is that the hocus pocus software sends a proprietary command to the disk to instruct it to activate/de-activate the HDD, and it also updates the partition table so it matches the new device size and layout. Somebody braver than me could probably intercept the SATA commands and write a tool that we can all use without getting an ISO from our favourite "supplier" (modern.ie? haven't tried to boot those on a real machine, but might work) for one hour.

---

### Post by radu.c on 2014-04-16
So much for that theory... this drive goes on the "**DO NOT BUY**" list. Formatting the HDD partition in place resulted in a corrupt ext4 that could not be mounted. Turning the partition into an extended one and creating an ext4 at an offset of 10 MB inside it resulted in disk reading errors in dmesg. It obviously does not behave like a normal drive. Oh, and the machine needed to be unplugged from the mains after that in order to see the drive again (or boot, for that matter).

---

