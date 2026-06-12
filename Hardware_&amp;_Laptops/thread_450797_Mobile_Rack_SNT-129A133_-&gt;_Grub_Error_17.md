---
title: "Mobile Rack SNT-129A133 -&gt; Grub Error 17"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by chiok on 2007-05-21
Howdy.

I've installed a mobile rack (SNT-129A133) that allows me to swap ATA hard drives using an ATA connection.  

When I've attempted to installed Ubuntu 7.04 beta, Debian 4.0, and Ubuntu Studio, the installer sees all my drives as SCSI drives (sda, sdb, sdc, sdd) even though there are one PATA drive, two SATA drives, and one ATA drive connected with the ATA mobile rack.  Despite the seeing them as SCSI drives, it installs fine.

The problem is when I attempt to boot up I get Grub Error 17 which is "Cannot mount selected partition". 

If I use a live cd, I sees and can mount all my drives (sda, sdb, sdc, sdd).

I have the MBR and Windows XP on the PATA drive and Ubuntu/Debian on the drive in the rack.

Any clue what I should do so I can boot up?

---

### Post by phredduk on 2007-05-28
Hi there

I think this may be something to do with the way Grub handles SCSI/SATA drives. (not sure if this is an Ubuntu issue or a grub issue..)

When i installed 7.04 a few weeks ago I got that Error 17 message and had to boot into a Live CD to correct the grub config.

Try editing /boot/grub/menu.lst (type the command 'sudo gedit /boot/grub/menu.lst') and scroll down to where the boot option for your partitions are. You may need to change the reference from something like (hd0,1) to (sd0,1). (sd0,0) is the grub equiv. of /dev/sda1, (sd0,1) is /dev/sda2 etc...

Also have a look in /boot/grub/device.map and see if hd0 has been mapped to sda1, if so then you can leave your menu.lst references as hd0,0 rather than change them to sd0,0 for example.
 
You may need to play around with it depending on your setup, but I'm confident that your Error 17 message is due to a bad reference in your /boot/grub/menu.lst

Good luck!

---

### Post by chiok on 2007-05-28
Thanks.  

I gave up on trying to fix grub.  Everything is fine if I install Linux on the ATA drive that isn't enclosed in the mobile rack.  *shrug*  It's a shame as I bought the rack so that I could "play with OSs".

---

