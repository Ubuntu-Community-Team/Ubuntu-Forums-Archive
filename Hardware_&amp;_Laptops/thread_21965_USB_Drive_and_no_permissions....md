---
title: "USB Drive and no permissions..."
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by pumaman on 2005-03-24
Bear with me as I am very new at this who linux thing...

I have an external USB drive that does appear, and I have managed to mount it. However, as soon as I do it locks me out and says that I have no permission to use the drive. I can't view anything on it.

If I log in to the command line as root, I can see everything just fine. However, it is my regular user that cannot access it. Why is this happening. I tried changing the permissions and the owner to myself (the "chris" user) but they never seem to change.

this is the command I use to mount it:

sudo mount -t ntfs /dev/sde1 /home/chris/usbhd1

and it does mount, but I cannot get into it.

Thanks for the help!

---

### Post by mercurus on 2005-03-26
Hi Chris

Is this a thumbdrive or similar, or an external HDD ?

Unless you've done something snazzy to a thumbdrive, it will be vfat, not NTFS. In fact, I'd recommend keeping it as vfat if possible, because permissions could be an issue when a thumbdrive is inserted into a machine with different users to your machine.

If it is an HDD as the mount-point would tend to indicate, I'd recommend a slight change. If you keep mounted filesystems under /media GNOME will cope better. If you want the conveniance of having the HDD's contents under your ~ dir, you can simply symbolic link to the mount point (eg. ln -s /media/usbhd1 /home/chris/usbhd1 ).

Assuming that it is an HDD that has been formatted with an NTFS filesystem, there are a few possiblities. Firstly, you might like to check that NTFS write support is safe - it wasn't last time I checked (a while ago now). If it isn't, you should pass the following option to mount:
```
-o ro
```

If you're satisfied that read/write NTFS is safe, then you should make sure that the filesystem is mounted owner by your normal user:
```
mount -o rw,uid=1000,gid=1000 /dev/sde1 /media/usbhd1
```
(assuming that uid and gid 1000 are for your normal user - as in the user you created during the Ubuntu install program)

Let me know if it works :)

Cheers
mercurus

---

### Post by pumaman on 2005-03-26
Awesome! It worked perfectly! Thank you!

It is an external USB hd formatted with NTFS. I am not too concerned about writing to it, as last time I checked that was unsafe.

I also mounted it in the /media folder like you suggested. Linux gets more useful everyday now...

Thanks again!

---

### Post by mila80 on 2005-04-04
Hi, 
   I had the same problem, and using mercurus's help, now I can read my USB HD,
However if I restart the system, I must re-do the mount operations.
Is it normal or there is a way to make it permanently?
I have an Other metter: I can't write in the drive.
How I can solve these problem???
Thanks,
Marco

---

### Post by mila80 on 2005-04-04
Those are the errors that chmod returns

root@ubuntu:/media # chmod +rwx usbhd1
chmod: ripristino dei permessi di `usbhd1': Read-only file system

---

### Post by lorap on 2005-04-06
hi friend!
it'll work!
first of all create a directory,say "usb-hd" in your home directory this way:

sudo mkdir /home/YourUserName/usb-hd

now let's get your hd connected:

sudo mount /dev/sr0 /home/YourUserName -t vfat -o umask=000

that's all 

now somw important tips:
i.if you're runnung not warty but hoary then you'll need to change "sr0" to "sda0".
ii.if you've formatted your usb hard drive as "ntfs" you'll need to write "ntfs" instead of "vfat".
have a nice day friend!
pavel

---

