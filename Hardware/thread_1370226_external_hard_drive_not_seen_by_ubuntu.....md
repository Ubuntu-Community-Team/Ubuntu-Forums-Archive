---
title: "external hard drive not seen by ubuntu...."
date: 2010-01-02
forum: Hardware
---

### Post by a-web on 2010-01-02
Having other issues with my installation (9.10) and so going for a reinstall.  But I can not get ubuntu to see the extrnal hard drive at all.  (sudo fdisk -l only shows my internal hard drive)  The hard drive works fine on a mac right here... and I can mount, etc. my USB thumb drive.

Ideas?

---

### Post by a-web on 2010-01-02
Can I just plug an ethernet cable from my ubuntu machine to a Mac and use that to backup my files?  Is that possible?

---

### Post by a-web on 2010-01-02
The answer to my last question is "yes".  Here's the method I used:
[http://www.moixo.com/es/sharing-files-folders-from-ubuntu-to-mac-os-x](http://www.moixo.com/es/sharing-files-folders-from-ubuntu-to-mac-os-x)

And I have given up on the external hard drive.

---

### Post by jc750kwak on 2010-01-02
My Vista laptop died last week and to get at the data on the hard disk I had to buy an external USB case with SATA controller. Once put into this the drive would not be recognised by Ubuntu. From this forum I found that:

1. Connect both USB connectors on the external unit as it needs 2x the USB supply to power the hard disk

2. Make sure I have ntfs-3g installed as this will allow me to access the NTFS filesystem used by Vista

3. Once it was being recognised by Ubuntu it still would not mount as the laptop crash had set some error flag on the drive. I had to force the mount using

sudo mount -t ntfs-3g /dev/sdc1 /mnt/laptopdrive -o force

afer "sudo modprobe ntfs"

This might help you

---

### Post by a-web on 2010-01-02
I am good up until "Once it is recognized by Ubuntu..."  that never happens.  But I found a work-around (with the Mac).  So thanks for the advice, but I am done with the external hard drive.

---

