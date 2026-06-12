---
title: "Increase size of persistence file?"
date: 2008-11-16
forum: General Help
---

### Post by homer693 on 2008-11-16
How do i increase the size of the persistence file(casper-rw ?) on my usb flash-drive for ubuntu?

---

### Post by homer693 on 2008-11-16
bump

---

### Post by C.S.Cameron on 2008-11-16
You can make a separate ext3 partition and label it casper-rw.
You then need to delete the existing casper-rw file.
You can also create a second ext3 partition and label it home-rw.

---

### Post by homer693 on 2008-11-16
> **C.S.Cameron said:**
> You can make a separate ext3 partition and label it casper-rw.
You then need to delete the existing casper-rw file.
You can also create a second ext3 partition and label it home-rw.

How do i do that?

---

### Post by C.S.Cameron on 2008-11-16
This is what I did on a 4 GB flash drive:

Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted the casper-rw file.
Shutdown, removed CD, rebooted.
Changes are persistent.

---

### Post by guimenez on 2008-11-26
thanks, it works well but now its very slow :(

i have 16gb flash, create 8gb(fat32), 8gb(casper-rw Ext3) and 2gb(home-rw) but now its very very slow.

can you help me please.

thanks

---

### Post by C.S.Cameron on 2008-11-27
I have found that sometimes they start out being slow to boot but after a few uses they speed up.
For a while it must have taken about 5 minutes to boot after installing ATI drivers.
Mine seems fast enough once it's running.

---

### Post by Marcelo Ruiz on 2009-06-18
Hi All,

I see this thread is quite old, so I know I'm taking my chances on getting any answers back...

I followed the instructions to create an Ubuntu 9.04 LiveUSB stick. I used NetBootin to create it and worked as expected. 

I do have problems with persistence. I am not able to find the 'casper-rw' file to replace it with a bigger file or to erase it to use the created the ext3 'casper-rw' partition.

I modified the syslinux.cfg file and added ' persistence' but still no luck.

Am I missing something? Can you tell me where the famous 'casper-rw' file is located so I can erase it?

Thanks in advance for your help!

Marcelo.

---

### Post by C.S.Cameron on 2009-06-25
It's been a while since I've used Unetbootin, but I don't think you get a casper-rw file out of the box with it, only with usb-creator. With unetbootin I think it is best to create casper-rw and home-rw partitions.
I am just now upgrading a flash drive to 9.04 and all my stuff is still there after the upgrade.

---

### Post by jake16424 on 2009-06-25
> **homer693 said:**
> How do i increase the size of the persistence file(casper-rw ?) on my usb flash-drive for ubuntu?

[http://www.pendrivelinux.com/usb-linux-mint-7-flash-drive-creation-windows/](http://www.pendrivelinux.com/usb-linux-mint-7-flash-drive-creation-windows/)

read, it says it at the bottom.

its all there, problem solved ;)

---

