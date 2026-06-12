---
title: "GRUB RESCUE! please help"
date: 2010-08-28
forum: Hardware
---

### Post by colladoguillermo on 2010-08-28
Hi Ubuntu people,
I've got quite a big problem here with my laptop, let me explain: It is a PackardBell EasyNote that came by default with two different hard disks. I had one with Windows 7 and the divided into two partitions. One was just NTFS with data (music, videos, pics, documents...) and the other partition in this second drive had Lubuntu.
The thing is I removed Lubuntu without thinking first. As I had installed it after Windows GRUB was doing the booting. I formated the disk completely from windows and now... i cant boot anymore.
If I try to boot up normally a message appears:
"error: no such device: 01e0d5a9-e8d9-4139-a9cb-bbdd066f64a7.
grub rescue>"
And of course I don't know what to do (im not exactly an expert)
I've tried to boot from different CD / DVD including Windows 7, Ubuntu (8.10, 9.10, 10.04...), Fedora, Linux Mint... and also from USB sticks... with the same outcome:
"No operating system found"
I even tried with System Rescue CD... but the same message appears.
Any help? I have no clue what to do. I would like to preserve the data (at least on the Windows 7 partition)... but if there's a way of fixing it that implies losing it... i guess I wouldnt mind too much.
Thank you!

[email]colladoguillermo@yahoo.com[/email]

---

### Post by Chris1274 on 2010-08-28
As long as your BIOS is working you should be able to boot from a liveCD or liveUSB. Go into the BIOS and make sure that the boot device manager isn't booting from the HD first. Change it so that either the USB device or CD/DVD drive is first on the list.

---

### Post by colladoguillermo on 2010-08-28
> **Chris1274 said:**
> As long as your BIOS is working you should be able to boot from a liveCD or liveUSB. Go into the BIOS and make sure that the boot device manager isn't booting from the HD first. Change it so that either the USB device or CD/DVD drive is first on the list.

I've done that, I boot from the USB / CD and it says "no operating system found" rather than "error: no such device:...." which is the message that appears when booting up from the HDD

---

### Post by Chris1274 on 2010-08-28
That's bizarre. Someone more knowledgeable than myself will have to step in here. I might try simply removing the hard drives and see if you can then boot up from the liveUSB. If you can at least get the thing running then you can always recover the data on the HDD using a hard drive enclosure kit.

---

### Post by colladoguillermo on 2010-08-28
> **Chris1274 said:**
> That's bizarre. Someone more knowledgeable than myself will have to step in here. I might try simply removing the hard drives and see if you can then boot up from the liveUSB. If you can at least get the thing running then you can always recover the data on the HDD using a hard drive enclosure kit.

Hope someone can help...

---

