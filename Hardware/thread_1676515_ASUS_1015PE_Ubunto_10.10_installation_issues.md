---
title: "ASUS 1015PE Ubunto 10.10 installation issues"
date: 2011-01-27
forum: Hardware
---

### Post by rex66 on 2011-01-27
Hi folks. I'm trying to install ubuntu netbook edition on my girlfriend's Asus 1015PE netbook and not having much luck. I've followed the instructions to the letter, or so I thought and I can not get it to boot from the flashdrive with ubuntu on it. I have gone into the Bios and changed the removable drive to the first option and it still booted to windows. I then disabled boot booster and it still booted to windows. I even disable the express gate software and still straight to windows? Am I missing a step?

TIA

Rex66

---

### Post by ajgreeny on 2011-01-27
Is there a key to press and get a boot menu for the netbook?  I have a netbook (re-badged MSI Wind) that needs F11 repeatedly pressed or the hard disk boots, even when the USB is first boot device.  have a good look at all the documentation you have for the machine.

Interestingly, a USB that I have with Puppy Lupu on it boots straight away with no key presses; it's the ubuntu family of USBs that need the F11.  Perhaps it's related to the isolinux boot system in some way; I have no idea, however.

---

### Post by rex66 on 2011-01-27
Hey thanks for the response aj. I'm not aware of any function key that needs to hit for the usb drive to boot, but I also tried disable the HDD as a bootable option and it just gave me an error message saying to insert a bootable disc/device. There doesn't appear to be anything wrong with the flash drive but I'm going to set up another one just to make sure. This is dissapointing. :(

---

### Post by ajgreeny on 2011-01-27
I assume you didn't just copy the iso file to the USB, but used **startup-disk-creator** or **unetbootin** to do the job?

---

### Post by rex66 on 2011-01-27
Correct. I followed the directions on the ubuntu site and used the Universal USB Installer from pendrivelinux.com.

I just got through trying a different flash drive to make sure that was not the problem. Still no success.

Anyone? Anyone?? Beuller??? :confused:

---

### Post by n2itive on 2011-03-03
You  need to spam the ESC key at boot

---

### Post by verdecit on 2011-03-14
> **rex66 said:**
> Correct. I followed the directions on the ubuntu site and used the Universal USB Installer from pendrivelinux.com.

I just got through trying a different flash drive to make sure that was not the problem. Still no success.

Anyone? Anyone?? Beuller??? :confused:

Short answer: Create a bootable SD memory card instead of a usb drive. It works on this netbook.

I have the same netbook and after a long time trying to install many different distributions of Linux (and other OSes) I found that only Jolicloud would make a bootable usb drive. However, the asus eee pc 1015pe seems to be able to boot anything just fine from an sd card. Suddenly, using an sd card, I could install any distribution I want. Currently running ubuntu 10.10. Try using a big enough sd card with the same methods used to make a bootable flash drive if you can and tell me how it goes.

---

### Post by skydiverQ on 2011-03-26
> **n2itive said:**
> You  need to spam the ESC key at boot

^^^^^ this worked for me, I was getting the same message mentioned above even though the USB key was inserted.  Hit the ESC key repeatedly at boot, and then I got a boot menu that let me select the USB key.

-sky

---

### Post by ymra on 2011-04-03
Go into the bios.  On the same screen where you change the boot order is an option called hard drive.  Select it and change drive order.  For some reason flash drives detect as hard drives.

---

### Post by pishta on 2012-04-05
Gotta love these netbooks that have no "Boot from USB" options. TRied it 10 different ways, it never sees the USB device whether its a USB flash drive, USB CDROM, USB HDD, etc. There is NO "boot to USB" option in the BIOS and the last resort is trying the SD card as mentioned in another post...No dice. Still no boot option. Fail.....And to top it all off, the netbook has an "unknown BIOS error" after multiple successful flashes to latest BIOS firmware. FAIL!!!

---

### Post by ymra on 2012-04-06
It doesn't detect as a usb hard drive just as a  hard drive.  Go into boot, boot device priority with the flash drive plugged in. change the order so that the flash drive is first.

---

