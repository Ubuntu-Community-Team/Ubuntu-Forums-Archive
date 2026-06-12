---
title: "Mounting USB Portable Hard Drive"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by Lord C on 2007-10-10
I checked Device Manager, and it shows my USB HDD as block.device /dev/sda

So I did this;
sudo mkdir /media/wdp0
sudo mount -t vfat /dev/sda /media/wdp0

And it gives the error "mount: /dev/sda: can't read superblock"

I have formatted the drive to Fat32.
It's a Western Digital Passport, 160gb.

I'm running Ubuntu PPC 7.01 on a G3 iBook.

I have even tried formatting the drive to ext3, but dmesg | tail still gives unable to read superblock

---

### Post by Lord C on 2007-10-10
Okay after some extensive reading, it seems the problem is that the iBook's USB sockets arn't giving enough power to the hard drive!

Unless there's a way to customise/edit the ammount of power being given to a specific device, then it looks like I'm going to have to buy a [USB 2.0 Power Booster Cable]("http://www.wdc.com/en/products/accessories.asp?ProdID=170").

They are cheap, but the only thing bothering me is that these take up 2 USB slots, and my mac only *has* 2 usb slots... meaning no external mouse for me! :/

Anyone know of a work around for USB power? Like disabling something?

Cheers

---

### Post by saitoh on 2007-10-10
I am not sure how to do this, but if you look in device manager there is an option that states the max power each device is allowed to have. You could try using the dual usb socket thing to get it mounted and then edit the amount of power the kernel allows it to have.

---

### Post by ttalja on 2008-04-28
I had the same problem. I am using Ubuntu 8.0.4 Hardy on a Dell Latitude C840 laptop with Pentium4 2GHz / a Intel 845 main board. I have a WD Passport of about 250MB. I am now borrowing a USB cable that takes the power from two USB slots and the drive is working without problems.

Cheers

---

