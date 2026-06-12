---
title: "SD card troubles with errors"
date: 2020-06-18
forum: Hardware
---

### Post by roadrash on 2020-06-18
I am having a awful time here working with SD cards in Ubuntu.  For some time now I can put a good SD card into a adaptor plug it into a usb port and its recognised and mounted.
Then if I decide to delete the card totally including all partitions or even just delete a large group of files, I will almost always get a error half way through and then cannot get out of it and there is no way of terminating it without damaging the file system on the SD card. If I delete each file one at a time its usually OK doing it that way.
It has become so bad and expensive I have had to install Windows which I hate using now on another partition on my hard drive just to do anything on USB pens and SD cards both which suffer from the same types of errors in linux during writing something.
I have tried numerous adaptors and cards and even tried different computers Desktop & laptops all with either Ubuntu or Linux Mint on them.
The damage usually, according to Gparted is damage to the partition table but trying to write another partition table results in yet another error or lock up just making it worse.
I am using the latest Ubuntu 20.04 at this time its no better than it was with 19.10.
Its starting to cost a fortune apart from the waste of time I have spent trying to recover them usually to no avail.  I use a lot of micro SD cards as I do a lot on a Raspberry Pi4 and I have to wipe a dash camera i recently bought.  I used to use unetbootin in linux but now recently Win32disk imager in Windows to write disk images.  My last failure was trying to wipe off a SD card with Raspian on it to put the latest Ambian emulator image on it.
I forgot (habit) stayed in Ubuntu and used Gparted to delete all partitions and make just one fat32 one to then write a fresh image of Ambian onto and I got the errors again right at the end and then had to kill the PC to reboot it, that's it damage done.  I always thought Linux was good for everything file system related but now I wonder.  Please Please Please can anyone tell me whats going on or what I could be doing wrong.  Is there anyway I can stop a errored operation without damaging the Card every time too?  Ive been using Ubuntu over 15 years now and sworn by and loved it until all this.

---

### Post by tea for one on 2020-06-18
I have also suffered a few errors with SD cards when reformatting with **gparted**.

However, so far, I've managed to save the card and use it again by using **gnome-disks**.

I couldn't explain the exact process but it is a result of trial and error.

For example, when a SD card is displaying unrepairable problems in gparted, I then use gnome-disks to delete and then format the partition.

Subsequently, the card is often re-recognised by gparted.

Also, I have used **mkusb** to **wipe** or **restore** a device.

I realise that my reply is imprecise but generally a combination of the tools can help recover your USB & SD devices.

---

