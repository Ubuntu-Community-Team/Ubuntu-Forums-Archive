---
title: "usb HD failed when xfer big files"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by Ti-Paul on 2005-04-20
I'm using an external usb HD on my Hoary installation (laptop).

Everything works fine when transferring "normal" files to it... (and it got automounted fine on my desktop!!... Whoohoo!)

But not for bigger files (starting at about 500Mb)... The copying timer keeps getting longer and longer, after awhile i got the "Error.......couldn't copy......."...

I then click Cancel and my usbdisk partition got unmounted by Linux...!!!
My usbdrive light keeps the light red (read/write activity)...

I tried copying a file ~250Mb... ok... Then tried another one ~270Mb... fine again... But if i select both than drag them to my usbdrive folder... The problem occurs...  ](*,) 

If i want to get back to normal, I totally unplug my usbdrive then plug it back...

Some infos:
USB Pocket Hard Disk Drive (2.5"), 40Gb formatted with one FAT32 partition.
No fstab entry since it's automagically detected and mounted by Ubuntu...
All this on a Dell INSPIRON 5150... Works great with Ubuntu..  \\:D/ 

I really need this to work since i have a couple of DVD iso files (~4.7Gb) to dump on this usbdrive...

Regards,
Ti-Paul.

---

### Post by diebels on 2005-04-20
Same problem if you mount manually?

---

### Post by Ti-Paul on 2005-04-21
Nope... I've put this in my fstab:

/dev/sda2  /media/usbdisk-1  vfat  noauto,umask=000,iocharset=iso8859-1,codepage=850,user,nosuid	0	0

Mount it manually, works pretty good with files or batch of files less than ~500MB...
But same problem for big stuff...  :|

---

### Post by dr_kabuto on 2005-04-21
Here I've a similar problem with a LACIE 200G USB hard drive, i've filed the bug #9825 but so far there's no response from devel.
I'll try to compile kernel 2.6.12-rc2 to see if the problem were solved since 2.6.10.

---

### Post by Ti-Paul on 2005-04-21
Aaaahhhh...

I'm not alone... phew!

OK, so i presume that i won't be using my usbdrive for a certain period of time...  :roll: 

I'll take a look somewhere else to see if there's any infos about this bug...

---

### Post by Ti-Paul on 2005-04-22
Just noticed that using the usbdrive on Windows XP does the same thing...

Tried formatting the drive in EXT2 but got same bug (big files xfer)....

The usbdrive keeps getting busy (red light) even if usb unplugged... Must cycle power off/on to get the usbdrive back to normal...

Humm... :-? 

Seem's like this is an OVERALL problem with USB Drive?... (or if anyone got successfull >500Mb files copying on this type of drive??)

---

### Post by Ti-Paul on 2005-05-04
BTW: The bug report (#9825) doesn't include good explanation... It should mention that BIG files (approx. >500Mb) put the system in an unstable mode. Device is unmounted, etc..etc...

No news on my side... Always getting the bug and regretting the purchase of the external HD casing... (I had an 40Gb 2.5" drive left)

---

