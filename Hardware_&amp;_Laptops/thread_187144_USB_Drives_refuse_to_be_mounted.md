---
title: "USB Drives refuse to be mounted"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by jet87 on 2006-06-02
I have USB thumbdrive and an old MP3 player that (in Windows) is seen as a USB drive.  Both of these are in working order, but for some reason Dapper is refusing to automatically mount either of them.  They show up in /var/log/messages, but what worries me is that /proc/bus/usb is empty; is that supposed to be?  Things worked fine in Breezy Badger, so I'm surprised that I'm having problems now.  What things can I do to fix auto-mounting?

Thanks in advance.

---

### Post by givré on 2006-06-02
what is the result of
```
modprobe -l |grep usb-storage
```
if it return nothing try
```
sudo modprobe usb-storage
```

---

### Post by jet87 on 2006-06-02
Thanks for the reply, givré.  I decided that with all the messing around I did with the system, I should just reinstall.  I did that, but first plugged everything in; everything was detected by the live cd and is now working happily.

Sorry for wasting your time, but thank you very much.

---

### Post by polo_step on 2006-06-02
[FONT="Courier New"]In a related problem, I see that some USB thumbdrives are recognized/mounted and some aren't.

I assume this is due to some formatting inconsistency between manufacturers.  The Patriot 512M just sat there and flashed and never mounted, while the PNY 512M was immediately mounted and accessed.  [shrug][/FONT]](*,)

---

### Post by jet87 on 2006-06-02
Ok, I guess I was premature in having things work out.  I just unmounted the drives, but when I connect them again the system refuses to mount them.

The output of the modprobe is "/lib/modules/2.6.15-23-386/kernel/drivers/usb/storage/usb-storage.ko"

Both lines in /etc/fstab are similar to this
"/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1"

Trying to mount gets me
"mount: special device /dev/sda1 does not exist"

Any clues as to what's happening?

---

### Post by jet87 on 2006-06-03
Ok, so I created /dev/sda1 and /dev/sdb1 for the devices, since for some reason it didn't exist.  The error I receive now is "mount: /dev/sda1 is not a block device."  I'm completely confused as to what I should do.

---

### Post by jet87 on 2006-06-03
Ok, I just rebooted.  With all the drives plugged in upon boot up they were detected.  Unmounted and remounted without issue one time.  Next, I "umount -a" then unplugged my thumbdrive and "mount -a."  The other drive was mounted without issue.  I plugged in my thumbdrive and did "mount -a" but received "mount: special device /dev/sda1 does not exist."  The directory /dev/sda1 does not exist, while both /dev/sdb and /dev/sdb1 do exist.  I created /dev/sda and /dev/sda1 and "umount -a" but receive "mount: /dev/sda1 is not a block device."  I'm absolutely stuck on what to do, as searching these forums and doing Google searches hasn't got me anywhere past this.

ETA:  I unplugged the device and did "mount -a" and received the same error, so it appears as if the drive isn't being "seen" by the system at all.

---

### Post by givré on 2006-06-03
[QUOTE=jet87]Ok, so I created /dev/sda1 and /dev/sdb1 for the devices, since for some reason it didn't exist.  The error I receive now is "mount: /dev/sda1 is not a block device."  I'm completely confused as to what I should do.[/QUOTE]

What did you do to create /dev/sda*, these are device, not directory, they should be created automaticly.
For exemple when i plug my usbkey, udev create automaticly the good device (/dev/sda), and this device is mount on a directory to be browsable

---

### Post by jet87 on 2006-06-03
I did "mkdir /dev/sdXN" for the missing devices.  What had me confused was when I "umount -a" the USB disks and another physical drive all umounted (thats supposed to be).  But the /dev/hda4 still exists while the /dev/sdXN don't.  

I booted the machine without any disks, but inserted the thumbdrive right before logging in and it mounted without issue.

---

### Post by givré on 2006-06-03
/dev/sda is not a directory but a block device. you shouldn't create this directory and you must not create this directory, it's why you have the error "mount: /dev/sda1 is not a block device." 
To make you sure of that, see the type of my sda:
```
flo@ubuntu:~$ ll /dev/ |grep sd
brw-rw---- 1 root plugdev   8,   0 2006-06-03 17:46 sda
brw-rw---- 1 root plugdev   8,   1 2006-06-03 17:46 sda1

```The first letter is for the type (d for a directory and b for a block device). It's quite difficult to understand when we come from windows, but the device and the directory where you browse this device are different (actually you mount the device on the directory). I was also a bit confused at beginning.

---

### Post by givré on 2006-06-03
One thing could be the order you plug your usb device. The first one will be set to /dev/sda and the second on to /dev/sdb automaticly by udev (see man udev to know more ) and you have only one line with /dev/sda in your fstab. 
The thing is you want to mount and umount with fstab, and i think that for thumbdrive and mp3 player it is not a good idea. 
You should less  gnome-volume-manager do the job (but first delete the /dev/sda line in your fstab), it should mount them automaticly (you could set the option somwhere in system>preference. 

That's just an advice...

---

### Post by jet87 on 2006-06-03
Wow, givré, removing the lines from fstab did the trick.  I guess I shouldn't have had the disks attached when I was instaling afterward.

Thank you so much for taking the time to help; it means a lot.

---

