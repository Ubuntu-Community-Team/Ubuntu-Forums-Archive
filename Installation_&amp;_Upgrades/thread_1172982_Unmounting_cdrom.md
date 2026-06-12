---
title: "Unmounting cdrom?"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by thorbjørn2 on 2009-05-29
Hi all - great forum. I'm new here on the forum and with ubuntu, and a complete newbie.
 
I am trying to install ubuntu from Unetbooting software. Its all working well except when the installer tries to partition the harddrive its comes with the error message: "failed to unmount the device: /cdrom " and diverts me back to the "partition manager". I'm on a laptop and the cdrom is broken (hence the unetbootin). What do i do? 
 
Cheers

---

### Post by atomizer on 2009-05-29
The /cdrom is mounted on the HD, witch need to be unmounted for patitioning. Thats when the error occurs.

If you can boot from usb, you can put the bootable image on usb and boot from there. your HD will be completely unmounted.


Maybe another solution is to create the partitions up-front, so you can skip the partitioning with your install. Don't know, haven't tried it yet.

---

### Post by thorbjørn2 on 2009-05-29
I can't boot from USB unfortunately. My bios don't support it. 
 
The live cd iso is installed on my c: partition which has windows installed. So I am not formatting or partitioning this part of the drive. Is that what you mean? 
 
I think the problem is that the installer is trying to see the cdrom but can't because it is broken. Is there someway i can trick the computer into thinking it does not have a cd-rom at all?

---

### Post by atomizer on 2009-05-29
no usb boot... too bad.

error is not about wrong detection of your broken cdrom-drive. I had the same problem, and my cdrom is working perfectly.
The error has been [reported]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/292493") in launchpad.

I think you could:
1) install ubuntu with [wubi]("http://wubi-installer.org/") into a windows-folder.

or

2) manually partition your drive from windows, and when installing ubuntu select "manual partitioning" when you get to the partitioning part, where you can assign your mountpoints to the appropiate partitions ( / , /home  and swap ) This way the installer doesn't have to alter your partition table, and should bypass the error point.

---

### Post by thorbjørn2 on 2009-05-29
Thanks for the advice. I'll try that.

---

### Post by Jeepfreak81 on 2009-10-27
> **thorbjørn2 said:**
> Thanks for the advice. I'll try that.


What ended up working for you?  This is the EXACT problem I am having right down to the broken CD drive and BIOS that does not allow USB booting.

---

