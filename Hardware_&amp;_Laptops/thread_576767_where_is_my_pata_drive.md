---
title: "where is my pata drive?"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by tomg66 on 2007-10-15
I have a dell precision 390.  I am attempting to attach a pata drive to the internal ide cable.  In the bios setup it is listed as pata0.  When I boot up fiesty though, it is displayed as /dev/sd[ab] not as /dev/hda.  This is important to me because I would like to manage the ata security settings on this drive, but when trying to do something like

hdparm --security-set-pass foobar /dev/sda

it returns that it is an inappropriate ioctl for that device.  I'm guessing here, but because it sees the drive as a 'scsi' device that the driver rejects  the security setting.

Any idea how I can do this?

TIA

tomg

---

### Post by Heresy on 2007-10-29
On my Dell laptop the drives showed as SCSI too.  
Here is what I did. 
This came from someone else in the forum.  
Worked like a dream for me.   


The problem is with the new "ata_piix" module. 
The solution is to blacklist this module and make a new initramfs:

Create a file, "blacklist-local" in /etc/modprobe.d! (sudo touch /etc/modprobe.d/blacklist-local) 

Edit the file (sudo gedit /etc/modprobe.d/blacklist-local) 
Write the following line in it, then save it: 
blacklist ata_piix 

Edit /etc/initramfs-tools/modules (sudo gedit /etc/initramfs-tools/modules) 

Add the following lines and save it:
piix 
ide_generic 
ide_cd 
ide_disk Execute the following command: sudo update-initramfs -u 
Update all files has /dev/sda (or sdb...) in /etc and /boot. You need to change them to hda (hdb...). These should be only the fstab and menu.lst files. But if you use UUIDs you don't need to modify anything. 
Restart your system. Be sure all edited files has a final blank line (enter).

After these steps you got old good hda disks and you can use hdparm as well.

---

