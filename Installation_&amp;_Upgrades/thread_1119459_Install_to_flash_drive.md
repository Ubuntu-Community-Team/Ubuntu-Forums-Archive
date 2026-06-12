---
title: "Install to flash drive"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by kazulk on 2009-04-08
I want to Install Ubuntu 8.10 to a 32gb flash drive I have. I want to do an actual install, not the live session thing. Can someone help me with this.

---

### Post by EXCiD3 on 2009-04-08
This shows you how to make a Ubuntu flash drive with persistent changes: [http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

---

### Post by Gresley on 2009-04-08
Not sure that the persistent install gets over your issue with the live session.

You can do a full linux install to the stick from the cd. Remove your hard drive, plug in the empty usb, then do a full install to the usb from the live cd.

---

### Post by Kevbert on 2009-04-08
The pendrivelinux persistent install is better than a full install as the USB drive is not continually written to (unlike a normal install to a hard disk which is 'on the fly'). All data can be saved to the USB drive but is normally saved at the end of the session. If you use the USB drive as if it was a hard disk the life of the drive is rapidly reduced (I've lost two drives by this method and eventually you'll be no longer able to read and write to them).

---

### Post by kazulk on 2009-04-08
I have tried what gresly said, and that doesn't work, When grub tries to load ubuntu it comes up with an error. Ill Try the persistant, also if I do that way, will I be able to install drivers to it and apps?

---

### Post by tlois on 2009-04-08
Use Unetbootin to install to flash drive (you can use the ISO you already downloaded, so you don't have to do that again) and then follow these instructions.  It works great and is easy.  On the step that says unzip to flash, just drag the package on the drive and unzip there.

[http://unetbootin.sourceforge.net/diskimg/readme.txt](http://unetbootin.sourceforge.net/diskimg/readme.txt)

that link shows you how t make a unetbootin install persistent

---

### Post by kazulk on 2009-04-08
well the unetbootin thing is just a live thing, and thats not what I want, I want to be able to install apps and drivers to it.

---

### Post by Khanon on 2009-04-08
Are you getting the "Error 21" error? Something I noted when I tried this exact same thing is that after you install 8.10 to your USB drive or Flash drive, you need to reset the computer, go into BIOS, go to Advanced Features, check your boot sequence, and make sure that your hdd is the first or second device and that the usb/flash drive is after it. If you see it in the list here, then it's otherwise fine.

Make sure it's in the slot when you boot up.

Such a simple thing, but it's what I had to do to get Kubuntu to boot from restart on my usb stick without Grub erroring on me.

---

### Post by kazulk on 2009-04-08
ok I did the persistant install, I read on a review of persistant installs that there is a command for syslinux to speed up the bootup, change it from -sf to -f or something like that, but the person didnt tell how, anyone know what that is about and how to do it?

---

### Post by Gresley on 2009-04-08
Kevbert is quite right on the full install, it will destroy the usb eventually by writing to it too often, the persistent live install gets around this and allows apps to be installed. I've not yet successfully managed to install any proprietary drivers to the persistent install.

Any help how to achieve this is hugely welcome.

---

### Post by tlois on 2009-04-08
that link shows you how to make unetbootin persistent.

---

### Post by kazulk on 2009-04-08
well proprietary drivers work for my 98gtx+ssc, also idk if it has anything to do with my bios but it doesnt always want to boot from the usb, like I cant do a restart and boot from it, I have to completely shut it down and do a cold boot

---

