---
title: "USB device stops responding"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by Leszek Tarkowski on 2005-06-07
Hi. After kernel upgrade to k-7 (2.6.10-34.1) my usb-flash-memory behaves strange.

After plugging in everything is fine - shows up, i can browse etc.

Problem is, that when i start to copy from/to device (using cp, or mc or nautilus) after few MB it "hangs". Nothing in dmesg or logs, nothing from apps (they just show still progress bar). All I can do is to remove device and use my flash memory with another computer :) What is more strange (at least for me) is that my external usb dvd-recorder works flawlessly. Another thing is that this pendrive is working on my laptop - but on laptop i have 686 kernel (it is Pentium-M based) and that is one diffrence everything else is the same. So i blame k-7 kernel.

I'v noticed (using ps fax) that scsi_eh_4, /usr/sbin/hald --drop-privileges, usb-storage and khubd are in state D (Uninterruptible sleep)....

Any help?

---

### Post by Leszek Tarkowski on 2005-06-08
Update - i check 386 kernel, and it is not working also. In warty and at the hoary rc everything was working flawlessly. Now is not.

---

### Post by andbert on 2005-06-09
I have a similar problem.
Couldnt find any solution though.

I ended up booting with an old kernel, and everything is back to normal

---

