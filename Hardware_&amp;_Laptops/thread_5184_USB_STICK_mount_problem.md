---
title: "USB STICK mount problem"
date: 2004-11-16
forum: Hardware &amp; Laptops
---

### Post by viorel on 2004-11-16
Unfortunately, ubuntu does not recognize my USB stick (Kingston DataTraveller 256 Mb). I tried to mount the device myself, with no succes. Does anyone know how i could do it? Thanks!

---

### Post by jdodson on 2004-11-16
plug in the usb stick.  here is the command i would use assuming you have only one usb storage device.

```
sudo mkdir /mnt/usb_stick
sudo mount -t vfat /dev/sda1 /mnt/usb_stick
```

if that doesnt work then paste in the last 30 lines of running 'dmesg' for us to see.

---

### Post by viorel on 2004-11-16
Already tried that, but didn't work. Than i thought of formatting the usb-stick using mkfs.vfat, and now it's automatically detected when i plug it in. Thanks anyway for your quick reply! Now I've got to figure out installing JBuilder9 (which seems to take it personal if you know what i mean) and got everything I need on my new ubuntu system.

---

### Post by TravisNewman on 2004-11-16
USB sticks "just work" on my PC. Have you tried "sudo modprobe usb_storage" and then just plugging it in?

---

### Post by viorel on 2004-11-16
[QUOTE=panickedthumb]USB sticks "just work" on my PC. Have you tried "sudo modprobe usb_storage" and then just plugging it in?[/QUOTE]
 As i said, i just formatted and it "just works" when i plug it in. Now i'm wondering how to umnount it without plugging it out. Any ideas?

---

### Post by TravisNewman on 2004-11-16
Ah sorry, I had this topic open a LONG time ago (before you posted your reply) and didn't think to refresh it.

You should get "eject" or "unmount" when you right click on the icon in Disks or Desktop

---

### Post by ghostrifle on 2004-11-16
I've got the same problem but reformatting didn't help:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=3479](http://bugzilla.ubuntu.com/show_bug.cgi?id=3479)

You need to apply this patch to the linux-sources package (2.6.8.2 or 2.6.9). Then recompile the kernel... install etc... then everything works.

Some USB-Sticks(and other usb devices) are broken ! They return wrong return codes so Linux doesn't know how to handle them. In the past, Linux "ignored" (like Windows still does) some return codes so everything just worked fine.  [-o< 

Bye, Alex

---

### Post by Marauder1 on 2004-11-16
For your info i had a Kingston DataTraveller myself too
and i got it back to the store. The darn thing can't boot
from the bios.  :-(

---

### Post by viorel on 2004-11-16
[QUOTE=panickedthumb]Ah sorry, I had this topic open a LONG time ago (before you posted your reply) and didn't think to refresh it.

You should get "eject" or "unmount" when you right click on the icon in Disks or Desktop[/QUOTE]
No problem! Already tried that, but I get the following error:
```
Unmount: /media/sda: device is busy
Unmount: /media/sda: device is busy
Error: umount failed
```
I also tried to remount as read-only and then unmount, but I still get the same error. How should I do it?

---

### Post by viorel on 2004-11-17
[QUOTE=viorel]No problem! Already tried that, but I get the following error:
```
Unmount: /media/sda: device is busy
Unmount: /media/sda: device is busy
Error: umount failed
```
I also tried to remount as read-only and then unmount, but I still get the same error. How should I do it?[/QUOTE]
 So, anyone can help with the above error?

---

### Post by zenwhen on 2004-11-17
[QUOTE=viorel]So, anyone can help with the above error?[/QUOTE]

Try closing all Nautilus windows. I sometimes have to do this to get the drive in my MP3 player to unmount.

---

### Post by viorel on 2004-11-18
[QUOTE=zenwhen]Try closing all Nautilus windows. I sometimes have to do this to get the drive in my MP3 player to unmount.[/QUOTE]
 Tried that already. Everything is closed, but still get the same error...

---

### Post by WW on 2004-11-18
Sounds familiar.  I think you have to kill famd,  remove the stick, and then restart famd.

---

### Post by WW on 2004-11-18
FYI: The relevant bug reports in bugzilla are 3168 and 2741.

---

### Post by viorel on 2004-11-18
[FONT=Verdana][SIZE=1]I finally found a way to do it, maybe handy for other people that can't umnount removable storage. Here's what I did:

I've added my removable storage dev. to /etc/fstab (sudo nano /etc/fstab). In my case, I had to add:
```
/dev/sda     /media/usb0     rw,user,noauto     0     0
```
Now, when I plug in my USB stick, it is automatically mounted(which also happened before), but it won't automatically unmount on unplug. That I do myself with the command:
```
sudo umount /dev/sda
```
It might be handy to disable auto-mounting, otherwise (if you forget to unmount after removing the USB dev.) it will get mounted again somewhere else on the next insert. You can disable auto-mounting in Computer --> Desktop Preferences --> Removable Storage.
In order to mount you should use:
```
sudo mount /dev/sda
```
Or just leave auto-mounting on, but remember to unmount every time you remove the USB storage dev.
Might not be the best way, but it works for me... [/FONT][/SIZE]

---

### Post by Original Brownster on 2004-11-27
Sometimes the 'fuser' command helps you find either the process id  or the user who has the device in use.  
HTH

---

### Post by phew on 2004-12-08
Yea, got that same problem here, although I HAVE sda1 in my fstab!

---

### Post by ohzopants on 2005-09-21
"umount -l /Stuff/usb" worked for me

---

### Post by TheWizzard on 2006-07-14
i had the same problems with my usb-stick (imation). 
re-formatting did the trick (i did that under windows :oops: ).

---

