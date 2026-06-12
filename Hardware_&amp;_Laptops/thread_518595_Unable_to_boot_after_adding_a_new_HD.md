---
title: "Unable to boot after adding a new HD"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by Twss on 2007-08-06
Hi all,
I'm not sure if there's any similar topic but I did actually search on it and couldn't see any... So sry if this is a duplicated topic.

I'm quite new to Linux. here is my problem:
I have two SATA HDs in my PC, two OSs: XP in the 1st partition of hda and Ubuntu 7.04 in the last partition of hda (hdb is just a storage). Everything is running well except when I try to add another new IDE HD to my PC, I can't boot into Unbuntu anymore, it hangs while it's loading devices (i guess), but i can still type, hit enter, ctl+alt+del, etc. 
I'm just wondering if we need to do anything before adding a new HD, or I need to reinstall Ubuntu after new HD is added?

Thx a lot,
Twss

---

### Post by RevThain on 2007-08-06
Ok, first of all, we need more info. Try this...

Assuming you use Grub, go to the line that boots ubuntu... Hit "e" and select the kernel line and hit "e" again... you should have at the end of that line the word "splash". Delete that word and hit enter. then hit "b" to boot it. now you will be able to "see" it load and if there are any error messages. Then post your findings.

---

### Post by Twss on 2007-08-06
Hmm... at the end of kernel line, there isn't a "splash", it ends with "root=/dev/sda3"
When I boot Ubuntu, I can actually see linux loading info, a lot of lines like:

[    4.222323] input: blah blah blah
[    4.283824] usb: blah blah blah
This is as normal as be4, but then it stops loading after a while. Here are the last three lines:

[    4.221591] input:use HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on use-0000:00:id.1-2
[    4.222435] usbcore: registered new interface driver usbhid
[    4.222479] driver/usb/input/hid-core.c: v2.6:usb HID Core dirver

seems like somthing related to usb...? wired

ps. I use XP boot.ini to load Grub

---

