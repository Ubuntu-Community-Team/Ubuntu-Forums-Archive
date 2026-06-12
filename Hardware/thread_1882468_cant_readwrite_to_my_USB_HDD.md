---
title: "cant read/write to my USB HDD"
date: 2011-11-17
forum: Hardware
---

### Post by gabrielaca on 2011-11-17
i mount the device, i open it, can see my folders, can play music and video, but [COLOR="Red"]_CAN NOT_[/COLOR] do write operations.

when i try to create a new folder/document its grayed out, when i try to copy files from my documents-downloads-music-pictures to the USB HDD i cant, a pop out windows comes up saying

Error while copying to "Ubuntu".
The destination is read-only.

so i wrigth click choose Properties, open,  click permissions, it say owner, i own it, click on file access, click on read and write, then apply permissions, works, when stops working i try to move a file to the uSB HDD and again: 

Error while copying to "Ubuntu".
The destination is read-only.

i tried opening via terminal going "sudo nautilus /media" then on properties change owner to Root but did not work either.


anyone have any idea what to do?):P

---

### Post by gabrielaca on 2011-11-17
also, enabled the sharing properties, it said i had not installed Samba so i did.

also, cant access the windows partion on the HDD (not the USB) its there, but cant see any file just folders.

---

### Post by marinara on 2011-11-17
does the USB connector look like this:
[http://lh6.googleusercontent.com/public/LvUYWfBlemBKHpkFSDcLi9aNbgun0ds460SfmqXDiaOFAUO3Ar_h4t0xdq9ZmRmHRQrwuVaRMpNUMXNbvITV7VooZh9svL4YJ95zX_xeW7FqR9FnCSIVzRJ7keHYzJ9bhzBjfR81hc83qwXBuMVRsK5JTYZVNhJChbLjlN0aAkSnIfMpqhkT-oPnUuE8KzL4ofK94pw](http://lh6.googleusercontent.com/public/LvUYWfBlemBKHpkFSDcLi9aNbgun0ds460SfmqXDiaOFAUO3Ar_h4t0xdq9ZmRmHRQrwuVaRMpNUMXNbvITV7VooZh9svL4YJ95zX_xeW7FqR9FnCSIVzRJ7keHYzJ9bhzBjfR81hc83qwXBuMVRsK5JTYZVNhJChbLjlN0aAkSnIfMpqhkT-oPnUuE8KzL4ofK94pw)
?

I'm just making sure, because some hard drives use ethernet to connect.
Please post brand and model.  Is it a USB thumb drive?  Does it have 'write protect switch'?

also, who installed the hard drive?  Did they use fstab?

You said you can access the HD, but not the USB?  Is this two separate problems?  I'm so confused.  Please just list each device you need help with.

---

### Post by gabrielaca on 2011-11-17
ok, my bad, its a external USB hdd and its conected via a usb cable  (the squareish one) its a seagate 1Tb, i scavenge my portable HDD and plug an internal HDD to the connectors, there is no write protect switch.

i can access the USB HDD, (which i use for backup) last week i did a backup on it (both Win and Ubuntu) but now it wont let me write to it, i get:

Error while copying to "Ubuntu".
The destination is read-only.

Ubuntu is the name to the drive.

also on my _**internal drive**_ cant access the Windows partition, (dual boot) i get the same error.

this is my cable.usb A to B [IMG]https://www.google.com/search?q=usb+a+to+b+printer+cable&hl=en&client=ubuntu&hs=z4r&channel=fs&prmd=imvns&source=lnms&tbm=isch&ei=jJ3FTpihIKWhsQLJ3vjICw&sa=X&oi=mode_link&ct=mode&cd=2&ved=0CDAQ_AUoAQ&biw=995&bih=695&sei=kp3FTrSxO6LJsQKwqL21Cw[/IMG]

---

### Post by marinara on 2011-11-17
are you using Lubuntu and PCManFM?  PCManFM for exploring the disk?

can you post contents of this file:  /etc/fstab

if you have this file present: */usr/share/pcmanfm/mount.rules* 
please post contents.

3rdly, r u using oneric?

---

### Post by marinara on 2011-11-17
also post contents of this directory
 /usr/share/hal/fdi/policy/10osvendor/

if there's an .fdi file in there, post the contents of that too, and the name of it

---

### Post by gabrielaca on 2011-11-17
geeez, i tag the post wrongly, sorry no Lubuntu, but Ubunto 11.10 (havent updated my sig.)

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1fc48d6d-5c68-4971-bdea-546bf3010611 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b23d20a3-80b2-49b4-9848-38079a3a978d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

i can get to /usr/share but no /pcmanfm/mount.rules it doesnt exist.

---

### Post by gabrielaca on 2011-11-17
ok no such folder /policy/10osvendor/

but there are:
 /preprobe/10osvendor/20libvsane.fdi  say (propietary scanner 1000 times)
and
/information/20thirdparty/20-lbmtp9.fdi ; 31-apple-mobile-device.fdi (names dvd and devices);  say (afc)

---

### Post by marinara on 2011-11-17
dang, I don't know much about nautilus... you're using nautilus right?

I need to know which file manager is auto-mounting the disk

---

### Post by Usksider on 2011-11-18
I had this exact same problem with my Samsung 1TB USB drive and think I've found a solution.

I installed NTFS-3G with Synaptic Package Manager (NTFSPROGS was removed by Synaptic at the same time) and was immediately able to write to  the USB drive, which I am currently using to back-up my system. :D

Hope this helps you too.

---

### Post by gabrielaca on 2011-11-23
thanks marinara, it worked for me, sorry for the delay to answer, but got caugth out in a lot of work.

---

### Post by wesleycj on 2011-11-23
Thank you for responding!  Unfortunately, this didn't seem to solve the problem.  I can write to the drive, but I can't pull many of the files off of it.  

Sorry, I forgot to mention that SOME of the files aren't locked.  The whole drive isn't the problem, just individual files and folders that I can't access due to permissions/ownership.  I've tried changing ownership for hours now, but nothing seems to take.

---

