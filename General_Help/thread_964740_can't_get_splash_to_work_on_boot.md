---
title: "can't get splash to work on boot"
date: 2008-10-31
forum: General Help
---

### Post by flowevd on 2008-10-31
hi

just upgraded, tho i had this problem before...

after grub i see the ubuntu logo with the oscillating orange bar underneath. when it usually goes into the phase where the bar grows from left to right, though, i always get a text output of what's being loaded. 

does anyone know how i can get the old splash back?


thanks
f

---

### Post by caljohnsmith on 2008-10-31
Did you by chance change any of your partitions, like resizing, especially your swap partition? If so, then you probably need to fix some files that use the UUIDs of your partitions, because your UUIDs would have changed with some partition changes. 

First do:
```
sudo blkid -c /dev/null
cat /etc/fstab
```
And make sure the fstab uses the correct UUID for your swap and other partitions. If it doesn't, let me know, because there are other files you will need to fix too. Another more obvious thing you could check is your menu.lst and make sure you have "quiet splash" at the end of the kernel line:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro [COLOR="Red"]quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
You can modify your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Good luck and let me know how it goes. :)

---

### Post by flowevd on 2008-10-31
thanks a lot for your help. turns out my fstab and the output from blkid do differ... though i'm not sure what to do with that information. here are the respective outputs.

```
 
sudo blkid -c /dev/null

/dev/sda1: UUID="ed52723b-360e-451a-bfc1-b854d49cf584" TYPE="ext3" 
/dev/sda2: UUID="19eca0f0-7cb2-481d-b5e3-55e4bf025026" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="78ae1f0e-5b43-4fdd-88d6-e1997e1fea0b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="e54f33a7-24c2-4788-b1a0-7c3f2513a884" TYPE="swap" 

```

and 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ed52723b-360e-451a-bfc1-b854d49cf584 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=16a10195-4562-44d8-8451-0fc409b48e82 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

```

i use the grub on my ubuntu partition (sda1) to boot to either intrepid or arch (which is on sda2 with a 'home' partition on sda4).

i never, ever would have thought this had anything to do with fstab. thanks! :-)

---

### Post by flowevd on 2008-10-31
btw, i do have 'quiet splash' in menu.lst too

---

### Post by caljohnsmith on 2008-10-31
OK, first do:
```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
And change your fstab as follows:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ed52723b-360e-451a-bfc1-b854d49cf584 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=[COLOR="Red"]e54f33a7-24c2-4788-b1a0-7c3f2513a884[/COLOR] none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
```
Next do:
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```
And change the UUID in that file to the same as the red UUID above for your swap partition. Next:
```
sudo update-initramfs -u -k all
```
And you should be all done. Restart, check if you get the splash screen OK, and let me know how it goes. :)

---

### Post by flowevd on 2008-10-31
you're a genius.
double thanks!

---

### Post by caljohnsmith on 2008-10-31
Glad it worked for you. Cheers and have fun Ubuntu-ing. :)

---

