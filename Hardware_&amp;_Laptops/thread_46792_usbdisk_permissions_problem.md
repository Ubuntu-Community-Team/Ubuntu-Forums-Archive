---
title: "usbdisk permissions problem"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by pierlo on 2005-07-06
Hi all!
i'm on  hoary and i am having a strange issue with my mp3 player (a Philips Gogear Hdd060, just to be precise): i used to plug it in and hal used to perfectly mount it and display an icon on the desktop and all the rest was just great.
i could use the player as an hardisk and i never had to setup a thing.
Until yesterday, when i connected the mp3 player to my laptop, which (for space problems) runs a hoary modified-base install (i started with the server install and then added what i needed, this not including hal, gnome-desktop and all the "advanced" stuff ) : since my laptop has no hal, i did 

```
$ sudo mount -t vfat  /dev/sda1 /media/usb
```

and it worked
i then copied some files on the player (always sudo-ing) and then unmounted it.

Once back to my pc, all seemed to work ok (hal mounted the usbdisk and the icon appeared on my desktop) : i could browse the mp3-disk files **BUT**  i couldn't write it anymore (the error displayed was : Not enough permissions. - not even if trying to copy the files with sudo!)

it's a really strange thing, it looks like if mounting "by hand" has changed something which now lets Hal mount the disk read-only.... yet i don't get it. 
I mean: is it possible? where the hell is this written? (moreover, the disk has a fat fs...!)

so if do a 

```
$ ls -l /media/usbdisk  
```

(on my pc, not the laptop) i get this:

```

lrwxrwxrwx  1 root   root      6 2005-06-15 23:12 cdrom -> cdrom0
drwxr-xr-x  2 root   root   4096 2005-06-15 23:12 cdrom0
drwxr-xr-x  2 root   root   4096 2005-06-15 23:12 cdrom1
lrwxrwxrwx  1 root   root      7 2005-06-15 23:12 floppy -> floppy0
drwxr-xr-x  2 root   root   4096 2005-06-15 23:12 floppy0
drwx------  5 pierlo pierlo 4096 1970-01-01 01:00 usbdisk

```

the only thing is: that pierlo is my typical user account (but it's got the same name as the account i use on my laptop...so i don't know [wheter this is possible] if that refers to the local pierlo or (?) to the laptop's user who mounted the usbdisk.....)

wow guys, i hope someone can make it a bit more clear, cause i'm sinking here...

 ](*,) 

thank you!

---

### Post by pierlo on 2005-07-06
no clues? please!!!

---

