---
title: "Usb disk write(speed) problem"
date: 2010-04-01
forum: Hardware
---

### Post by svennils on 2010-04-01
I've recently got problems when writing to my usb2 disks. 
the write operation fills the buffer, then stops, until dmesg shows something like: 
" 2269.060343] usb 1-7.1: reset high speed USB device using ehci_hcd and address 8"
It then resumes. And on it goes. Write speed is abysmal, 2.5mb/sec.

My 500gb disk is ok, 18mb/sec read/write
My 1000 and 1500gb WD disks have the above problems of recently.
Read speed is ok.
Same disks in win7 on same computer(dualboot) give 30-50mb/sec write speed.
What's going on?
Mounting manually with -o async does not help.
Googling it shows i'm not alone, but no solutions that work.

This is on a freshly installed and updated box with 10.04

---

### Post by svennils on 2010-04-01
Ok, tried it on my asus 900, with a stone old eeeubuntu 8.10.
it works flawlessly, no usb resets and about 15 mb/sec on a mix of files sizes.

Used to work on my laptop with 9.04
This probably got broken some updates ago, and i have not been writing much data to the disks so it's gone unnoticed for some time. 
Any ideas anyone?

---

### Post by IcarusR on 2010-04-01
Ubuntu 10.04 is beta for testing, not released yet. I suggest you use a stable released version, 9.10 or earlier.
However if you have issues with 10.04 then you should post in the "Development & Programming > Lucid Lynx Testing and Discussion" forum

[http://ubuntuforums.org/forumdisplay.php?f=377]("http://ubuntuforums.org/forumdisplay.php?f=377")

---

### Post by svennils on 2010-04-01
woopsy, my bad. 
The box in question runs 9.10, i'm getting a bit confused between versions (only got 5 boxes/portables with different versions).
And my laptop with 9.04 where the disks used to be connected has the same behavior. I could not even run the mkfs.ext3 to completion, too many usb device resets and timeouts.

---

