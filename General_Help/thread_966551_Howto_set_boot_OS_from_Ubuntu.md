---
title: "Howto set boot OS from Ubuntu?"
date: 2008-11-01
forum: General Help
---

### Post by randomAccess on 2008-11-01
SUSE users had a very nice application - one could choose which OS (in dual boot environment) will boot on the next system boot.

Is this possible to do this from Ubuntu Intrepid? :confused:

---

### Post by Idefix82 on 2008-11-01
You mean, which OS is preselected in GRUB when you start your computer? You can do that by editing the file menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
and then find the line which says
```
default=0
```
and change 0 to the number of the entry that you want to be preselected. You can also change the timeout value, which is the number of seconds after which the default selection is booted.

---

### Post by randomAccess on 2008-11-01
Hm well yes but this is all permanent. I don't want to do it permanently, just from time to time (when I rest from work I boot to Windows to play games). Similar to boot-once (I think this is the name) grub's directive, but this boot-once didn't work for me so I need the similar tool to the one in SUSE.

---

### Post by randomAccess on 2008-11-01
This is the link that was supposed to solve my problem: [http://sidvind.com/wiki/GRUB:_Boot_another_OS_once](http://sidvind.com/wiki/GRUB:_Boot_another_OS_once)

It says that it would be enough to type the command 
```
echo "savedefault --default=2 --once" | grub --batch
reboot
```

but when I type this I get an error:
```
$ echo "savedefault --default=2 --once" | grub --batch
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> savedefault --default=2 --once
**Segmentation fault**
```

:confused::confused:

Here's my menu.lst

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f94d5941-ca78-4e84-9f4c-6b967a4959ba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f94d5941-ca78-4e84-9f4c-6b967a4959ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f94d5941-ca78-4e84-9f4c-6b967a4959ba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f94d5941-ca78-4e84-9f4c-6b967a4959ba ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f94d5941-ca78-4e84-9f4c-6b967a4959ba
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows XP Professional x64 Edition
root		(hd0,3)
savedefault
makeactive
chainloader	+1
```

I tried to change the default to 2,3 and 4, but all in vain. 

Hope someone can help :(

---

