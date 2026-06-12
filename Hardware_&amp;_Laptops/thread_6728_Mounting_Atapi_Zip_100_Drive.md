---
title: "Mounting Atapi Zip 100 Drive"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by pinoakz on 2004-12-01
Hi,
So far I have had no luck in mounting my Atapi Zip 100 Drive and need help in getting it mounted. So far I have:
1) Typed "dmesg" in the terminal and have seen the drive listed as hdb atapi Zip.
2) Altered fstab file with the line "/dev/hdb       /mnt/zip        vfat    rw,user,noauto 0 0" after creating the necessary zip directory in the mnt directory.

After saving the fstab changes the **Disks** window will show an icon for the Zip drive, but clicking on it brings up a message box that says "/dev/hdb does not exist". I have tried altering the fstab entry to /dev/hdb1 thru /dev/hdb4 and rebooting with no success. With Fedora Core 3 I was able to get it mounted using the same line in fstab with /dev/hdd4 entry. Can anyone help me with this? Thanks.
Regards,
pinoakz

---

### Post by scoon on 2004-12-01
Hey there, 

You need to have scsi emulation module loaded in the kernel and the low level driver for the zip drive as well.  Once those things are loaded, your zip will almost certainly work just fine. 


scoon

---

### Post by pinoakz on 2004-12-01
Thanks for the reply, how do I go about doing the things you mentioned. I am fairly new to Linux.
Regards,
pinoakz

---

### Post by wallijonn on 2004-12-01
[QUOTE=pinoakz] Altered fstab file with the line "[COLOR=Red]/dev/hdb       /mnt/zip        vfat    rw,user,noauto 0 0[/COLOR]" after creating the necessary zip directory in the mnt directory.[/QUOTE]

Shouldn't that be [COLOR=Red]/dev/hdb /**media**/zip vfat rw,user,noauto 0 0[/COLOR] ?

You may need to [COLOR=Red]sudo gedit /etc/modules[/COLOR] and add[COLOR=Blue] zip[/COLOR] to the end of the list. (conjecture),

---

### Post by randy on 2004-12-02
It doesn't need to be /media/zip thats just the default in ubuntu.  You might not want to change it if you've got shell scripts that depend on it.

---

### Post by wallijonn on 2004-12-02
[http://www.faqs.org/docs/Linux-mini/ZIP-Drive.html](http://www.faqs.org/docs/Linux-mini/ZIP-Drive.html) : > The good news about this drive: no kernel modules or modifications are needed to support it. It looks to the kernel like an IDE hard drive. It worked for me with no effort with kernel 2.0.31 and 2.0.32.

The bad news about this drive: because it doesn't use ATAPI, you can't use the SCSI-to-ATAPI translation, which means you can't use mtools to write-protect disks (or to eject them, for that matter).

Therefore he's going to have to work with fstab and modules.conf. First he's going to have to format the drive before he can mount it.

If he installed the OS with the zipdrive already connected, then chances are that there is a zip folder in /dev. if he uses /mnt as a mount point then he will have to do manual mounts and umounts. if it has in deed been defined as "zip," then he should be able to [COLOR=Green]cd /etc, modprobe zip, update-modules[/COLOR] and add "zip" to [COLOR=Green]/etc/modules.conf[/COLOR], then reboot.

the question is, is there a folder named "zip" in /media?


.

---

### Post by pinoakz on 2004-12-03
Thanks for all the replies. I entered "modprobe zip" in the terminal window and the return was "module zip not found". Adding zip to the list in the file /etc/modules does not change the original error message of "device hdb does not exist".
Regards,
pinoakz

---

### Post by scoon on 2004-12-03
Hey there, 

This helped me to get my zip drive working when I used it.  [http://www.tldp.org/HOWTO/text/ZIP-Drive](http://www.tldp.org/HOWTO/text/ZIP-Drive)

scoon

---

### Post by Petaris on 2005-01-19
[QUOTE=pinoakz]Thanks for all the replies. I entered "modprobe zip" in the terminal window and the return was "module zip not found". Adding zip to the list in the file /etc/modules does not change the original error message of "device hdb does not exist".
Regards,
pinoakz[/QUOTE]
 use the ide-floppy module

---

### Post by Campitor on 2005-01-27
[QUOTE=Petaris]use the ide-floppy module[/QUOTE]
 Hi:

  I've been having trouble with my ATAPI IDE Zip 100 drive.  I have included the ide-floppy module to modules.config, created a /media/zip0 directory, edited fstab to 
/dev/hdd4, /media/zip0, vfat, rw,users,noauto 0 0

and I can mount and read my Zip drive now...and gnome puts the icon on the desktop and all.  The problem comes when I want to eject the bloody disk...

I've done two things...right click on the zip icon in nautilus and selected "Eject disk" and also typing "eject /media/zip0" (or its equivalent eject /dev/hdd4) in a command prompt.  In both cases the disk starts spinning, but the disk will not eject.  If I press the little LED botton, I cannot retrieve the disk.  For some reason, it locks it ini there.  I have to restart my computer and get the disk before UBUNTU loads the GDM.  Please help...I really need to have access to my Zip drive.

Thanks

Campitor

---

### Post by scoon on 2005-01-27
hey there, 

before using eject try and use umount first.  I am running hoary and have the same problem w/ some of my removable media.  The only thing I have found to eject them is to unmount them from a shell first.  I know this is not such a hot solution but I haven't spent the time to figure out what the problem is. 



scoon

---

### Post by pseudonym on 2005-01-27
Yes, 'umount /dev/hd** or /media/zip0' is really the only solution-that's the way it is in Linux with all removable media AFAIK. If you remove stuff without unmounting you run the risk of losing data.

Sometimes you will find that your disk still won't come out despite issuing the umount command. In that case, you'll need to do what's called a 'lazy' unmount -

umount -l /dev/hd** 

Since discovering that I haven't had any problems with not being able to get disks out.

---

### Post by Campitor on 2005-01-27
[QUOTE=pseudonym]Yes, 'umount /dev/hd** or /media/zip0' is really the only solution-that's the way it is in Linux with all removable media AFAIK. If you remove stuff without unmounting you run the risk of losing data.

Sometimes you will find that your disk still won't come out despite issuing the umount command. In that case, you'll need to do what's called a 'lazy' unmount -

umount -l /dev/hd** 

Since discovering that I haven't had any problems with not being able to get disks out.[/QUOTE]
 Thanks !!!! It worked...I found the solution.  If I do:

mount /media/zip0 

and then do:

umount /media/zip0

The disk will not eject...but, if do:
  mount /media/zip 
and 
  umount /media/zip 

  I have a symlink from /media/zip to /media/zip0;  then the disk ejects fine.  You were right, I cannot do an eject by right-clicking on the zip disk icon, that locks the disk in there and it is impossible to get out.  But if I unmount it from a command prompt or by pressing Alt-F2 and entering: umount /media/zip  I can then eject the disk with the LED botton.

thanks a lot for all your help...I've tried a bunch of Linux distros, and although I find Ubuntu a lot harder to work with than any of the other distros, the people in these forums have made me want to stick with it for a long time.  Thanks

Campitor

---

### Post by pseudonym on 2005-01-27
Glad to be of help :)

Btw, you should be able to use the 'eject YOUR DEVICE NAME or MOUNTPOINT' command after unmounting your disk. Saves reaching down to press the button :)

I updated the zip drive howto with unmount/eject info too, btw.

Ubuntu's the first Linux distro I've had a serious go at, and I've had my fair share of configuration issues, too (just lately with the nvidia 6629 driver). Sometimes I wonder 'why did I ever move from win xp, where I could do everything so much easier?' But the added security, open source philosophy and, as you said, the excellent support available for Ubuntu, have all made me want to persevere. I don't think I'll be going back :)

---

### Post by albersag on 2005-01-27
Does anyone know how to get working a zip 250 USB on ubuntu. 

usb 1-1: USB disconnect, address 3
usb 1-1: new full speed USB device using ohci_hcd and address 4
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: IOMEGA    Model: ZIP 250           Rev: 31.G
  Type:   Direct-Access                      ANSI SCSI revision: 00
sda: Spinning up disk...............................................<5>Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
usb-storage: device scan complete
usb 1-1: USB disconnect, address 4
usb 1-2: new full speed USB device using ohci_hcd and address 5
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
  Vendor: IOMEGA    Model: ZIP 250           Rev: 31.G
  Type:   Direct-Access                      ANSI SCSI revision: 00
sda: Spinning up disk.....................................................................


But /dev/sda mounting does not work.


Thanks

---

### Post by Petaris on 2005-01-31
[QUOTE=Campitor]Hi:

  I've been having trouble with my ATAPI IDE Zip 100 drive.  I have included the ide-floppy module to modules.config, created a /media/zip0 directory, edited fstab to 
/dev/hdd4, /media/zip0, vfat, rw,users,noauto 0 0

and I can mount and read my Zip drive now...and gnome puts the icon on the desktop and all.  The problem comes when I want to eject the bloody disk...

I've done two things...right click on the zip icon in nautilus and selected "Eject disk" and also typing "eject /media/zip0" (or its equivalent eject /dev/hdd4) in a command prompt.  In both cases the disk starts spinning, but the disk will not eject.  If I press the little LED botton, I cannot retrieve the disk.  For some reason, it locks it ini there.  I have to restart my computer and get the disk before UBUNTU loads the GDM.  Please help...I really need to have access to my Zip drive.

Thanks

Campitor[/QUOTE]
 Yeah, that one pisses me off too.

You can use 'umount -l /media/zip'

That is a lowercase L it stands for lazzy.  It seems that it is not being told when the cache has finised writing to the disk.  I also wish there was a way that it would keep the hdb4 node as the disk likes to be hdb4.  The only solution I have found for having this created automatically is to have a zip in the drive when booting.  Otherwise you can get udev to create it by trying to mount hdb and it will fail but create the hdb4 node (you must have a disk in for this to work).

I have a zip250 by the way.

---

