---
title: "rename usb partition"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by DSABH on 2006-06-25
hey,

ive got an external hard disk which i linked via usb.
i formatted the partition to ext3 and set the user rights so it works fine.
but the partition label sux, it says 'usbdisk' but i want it to have another name.

does anyone know how to do this?

---

### Post by FuturePast on 2006-06-25
[QUOTE=DSABH]
does anyone know how to do this?[/QUOTE]

I don't know how to do this, but the general area of the problem is udev, pmount and hald.

BTW, what exactly is wrong with the name usbdisk? :)

---

### Post by .t. on 2006-06-25
Just rename the folder where it is mounted; usually you can just right-click and select rename.

---

### Post by DSABH on 2006-06-25
thanks for the prompt answer..

here we go

i tried to rename under

computer:///  -> via gui

the option rename is available, however, if i type 'Garbage' it tells me that i cant rename it

under /media/usbdisk/ the option isnt available so i tried the terminal with

```
sudo cp /media/usbdisk /media/Garbage
```

it tells me that it left out the directory 'usbdisk'

basically cuz cp does only rename files i guess..

any other suggestions ??

pleaazz .. thanks :)

---

### Post by .t. on 2006-06-25
I suggest that you do, in the terminal, "sudo nautilus". Click "Computer", and try to rename again. That way you're doing it with root privilages.

---

### Post by FuturePast on 2006-06-25
Have a look at this:

[http://www.mythic-beasts.com/~mark/random/hal/](http://www.mythic-beasts.com/~mark/random/hal/)

---

### Post by coffeecat on 2006-06-25
[QUOTE=DSABH]does anyone know how to do this?[/QUOTE]


Yes. You need to use the 'e2label' command from a terminal. Type 'info e2label' or 'man e2label' for all the options.

You'll probably have to do 'sudo e2label', but it's a handy little utility.

---

### Post by chele on 2006-08-15
> **coffeecat said:**
> Yes. You need to use the 'e2label' command```
:~$ ls -al /media
drwx------  3 chele chele  8192 1969-12-31 16:00 usbdisk
drwx------  6 chele chele 32768 1969-12-31 16:00 USB DRIVE

```How is this done permanently? In my case, the 'USB DRIVE' is a USB HD and the 'usbdisk' is a digital Camera. It would be cool if the names of the actual devices showed up.  ```
 idVendor           0x07b4 Olympus Optical Co., Ltd
  idProduct          0x0109
  bcdDevice            1.00
  iManufacturer           1 OLYMPUS
  iProduct                2 IR-300
``` ```
 idVendor           0x07b4 Olympus Optical Co., Ltd
  idProduct          0x0310
  bcdDevice            0.00
  iManufacturer           1 OLYMPUS
  iProduct                2 S-HD-100
```is there some way to tell hal/udev that 0x0109 should mount as IR-300 and 0x0310 as S-HD-100? I don't want to just use /dev/sda1, as that may be used if I plugged in a USB flash drive at some point.

And what is with the 1969 file date on those mounts?

---

### Post by chele on 2006-08-15
> **FuturePast said:**
> Have a look at this:

[http://www.mythic-beasts.com/~mark/random/hal/]("http://www.mythic-beasts.com/%7Emark/random/hal/")Yes, that looks like it. But where does the udi (“unique device identifier”) come from?

---

### Post by chele on 2006-08-15
> **chele said:**
> ...where does the udi (“unique device identifier”) come from?[B]System > Administration > Device Manager

[/B]With that information, and the instructions given by Mark at mythic-beasts, I am most of the way there. I created a 's-hd-100.fdi file with the following content: ```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/volume_uuid_286A_14F0">
      <merge key="volume.policy.desired_mount_point" type="string">S-HD-100</merge>
      <merge key="volume.policy.mount_option.iocharset=utf-8" type="bool">true</merge>
      <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
    </match>
  </device>

</deviceinfo>
```It now mounts under /media/S-HD-100 & shows that as the Nautilus window title. 

But. The desktop icon still shows as 'USB DISK'.

---

### Post by mobilehavoc on 2006-09-04
In case you or someone reading this thread is curious, this link shows all - nice and easy. Worked like a charm.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by chele on 2006-09-04
> **mobilehavoc said:**
> In case you or someone reading this thread is curious, this link shows all - nice and easy. Worked like a charm.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)Yes! That is much more elegant then hacking together .fdi files for each device. mlabel to the rescue!

---

### Post by gkokaisel on 2007-03-16
> **coffeecat said:**
> Yes. You need to use the 'e2label' command from a terminal. Type 'info e2label' or 'man e2label' for all the options.

You'll probably have to do 'sudo e2label', but it's a handy little utility.

That worked great for changing ext3 but do happen to know how to change fat filesystems? I parted my 4 gig usb into 2, 2 gigs fat 16,s, and I want to name each part something other than the default usb1 and usb2. It has to be fat 16 because of some stuff I want to run off there. 

Not really a priority but if anyone happens to know, I would much appreciate it (too bad gparted doesn't include a renaming option).

---

