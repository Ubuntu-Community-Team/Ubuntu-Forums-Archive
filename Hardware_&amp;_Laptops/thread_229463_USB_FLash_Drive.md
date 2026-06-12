---
title: "USB FLash Drive"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by Ryan H on 2006-08-04
I was wondering what company, or brand of USB thumb/flash drives are compatible with Ubuntu, or Linux in general. I'm probally going to get a 1 GB drive. Such as
[http://www.supermediastore.com/pqi-u230-traveling-disk-1gb-usb-20-usb-flash-drive.html](http://www.supermediastore.com/pqi-u230-traveling-disk-1gb-usb-20-usb-flash-drive.html)

Any suggestions?

-Ryan H

---

### Post by zxee on 2006-08-05
I like sandisk but that's just a personal preference-almost any recent usb flash drive should work.

---

### Post by cantormath on 2006-08-05
> **zxee said:**
> I like sandisk but that's just a personal preference-almost any recent usb flash drive should work.

sandisk works for me too.......:KS

---

### Post by marx1984 on 2006-08-06
Imation has specific support for linux. Especially the HMDS-01GC Model. It worked like charm. All I had to do was add scsi support, human interface device support and usb mass storage device support to my custom kernel. It comes formated as fat32 so just just modprobe vfat. Then mount -t vfat /dev/sda1 /media/usbflash. you must create usbflash in the media directory before mounting anything. It has to exist before you can use it in an argument. Also, you can edit your fstab to automount your usb flash drive. let me know if you require further assistance.

---

### Post by Greyhair on 2006-08-07
Corsair 1GB Flash Voyager USB drive works a treat!

---

### Post by GameGod on 2006-08-07
I think it's safe to say that every USB flash drive is compatible with Ubuntu/Linux.
(The whole point of them is to act as a "USB Mass Storage Device", so you don't need to install drivers... They "just work"...)

If anyone has found a drive that *doesn't* work, I'd be interested in hearing about it.

---

### Post by Lucidio on 2006-08-07
> **GameGod said:**
> I think it's safe to say that every USB flash drive is compatible with Ubuntu/Linux.
(The whole point of them is to act as a "USB Mass Storage Device", so you don't need to install drivers... They "just work"...)

If anyone has found a drive that *doesn't* work, I'd be interested in hearing about it.
-----------------------------------------------------------------
I´ll take your word! My usb flash drive doesn´t work on Ubuntu.
For a strange reason ubuntu recognize the device but when i try to open it, the system give me an error message. Unfortunally i´m not in ubuntu right now, so i can´t give you the message.

My device is a 1 gb usb 2.0 flash disk usb device formated in fat32. I dont know the brand, but i´m almost sure that worked once under breezy.

if anyone can give me a light whith my problem y will be very thankfull...

---

### Post by brussel on 2007-07-01
> **GameGod said:**
> I think it's safe to say that every USB flash drive is compatible with Ubuntu/Linux.
(The whole point of them is to act as a "USB Mass Storage Device", so you don't need to install drivers... They "just work"...)

If anyone has found a drive that *doesn't* work, I'd be interested in hearing about it.

Corsairs 16GB doesn't work. You have to boot the system with it in and no other USB device connected to get it mounted. If you pull it out you have to reboot it over. Others have also tried to use it for their boot drive but apparently it doesn't work for that either.

Of course I'd like you to prove me wrong...

---

### Post by kserg on 2007-09-12
> **brussel said:**
> Corsairs 16GB doesn't work. You have to boot the system with it in and no other USB device connected to get it mounted. If you pull it out you have to reboot it over. Others have also tried to use it for their boot drive but apparently it doesn't work for that either.

Of course I'd like you to prove me wrong...

Seems to not work... Anyone else found a solution? 8gb works ok?

EDIT: I guess installing kernel 2.6.22 makes it work... still didn't get it to work 100% ifconfig shows everything ok, however, still no go with network. But card issue seems to be solved under 2.6.22-11.

---

