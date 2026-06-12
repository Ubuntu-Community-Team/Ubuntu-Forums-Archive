---
title: "Booting from usb-stick compared to cd-rom. Any differences?"
date: 2008-08-05
forum: General Help
---

### Post by ayampanggang on 2008-08-05
Just a few minutes ago i tried installing debian from an install cd-rom, which failed because the system didnt recognize my cd rom drive.

Later i tried to install from a usb stick-i simply dd'ed the whole debian iso image into an unformatted partition which i had previously created on the usb stick.The operation went successful, as i can mount and browse the content of this newly created partition from a file browser. The content appears exactly the same as one in the cd-rom i burned so i concluded the copying operation using dd was successful.

Last, i set the bootable flag for this partition.

And then i boot the box using this usb stick's partition, only to discover: "invalid bootable partition"

Does the computer handles USB-booting differently than CD-ROM? When installing using usb-stick, does the computer expects a different format other than raw iso images?

Thank you.

---

### Post by mixmaster on 2008-08-05
Bootable usb sticks require some files to be differently located and may need a FAT based boot partition.  There are various FAQs around for building bootable USB sticks (with or without persistent data).  The exact procedure seems to be distro and release specific (eg a bug prevents persistent data on some Ubuntu releases) so you will need to dig around a bit, but it can be done.

---

### Post by ayampanggang on 2008-08-05
i see, so that's it

thank you for your clearance, because i thought apart from differences of media, it would be exactly the same

---

### Post by ProbablyX on 2008-08-05
I followed the guide here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and it worked very well. Just use the GUI app and it's done (more or less :))

NOTE after you've installed, your CDROM drive wont work unless you go to /etc/fstab and comment out the line:
> 
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


as it will set your usb stick as cdrom0. After thats commented out it works fine!

---

