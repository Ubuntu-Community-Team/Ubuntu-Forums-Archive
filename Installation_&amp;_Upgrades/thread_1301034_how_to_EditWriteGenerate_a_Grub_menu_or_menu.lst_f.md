---
title: "how to Edit/Write/Generate a Grub menu or menu.lst file GRUB 0.9x"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by meka4996 on 2009-10-25
Tutorial for how to Edit/Write/Generate a Grub menu or menu.lst file for GRUB version 0.9x [GRUB Legacy] for Ubuntu 9.04, 8.10, 8.04, ... (Not for Grub2 in 9.10)
It basically looks like this... 

(this is a sub menu, not the Main menu)
### The Start of the Grub menu.lst file
# skipping default settings...

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		6bb59283-ffd7-4732-b185-f81cb3d14bc9
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6bb59283-ffd7-4732-b185-f81cb3d14bc9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		6bb59283-ffd7-4732-b185-f81cb3d14bc9
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6bb59283-ffd7-4732-b185-f81cb3d14bc9 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS

title		Main Menu (/dev/sda)
root		(hd0)
chainloader +1

### The End of the Grub menu.lst file


(this is the Main menu, not a sub menu)
### The Start of the Grub menu.lst file
# skipping default settings...

# OS installations...
title		Ubuntu 9.04 (/dev/sdb13)
root		(hd0,12)
chainloader +1

title		Ubuntu 8.04 (/dev/sdb8)
root		(hd0,7)
chainloader +1

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

### The End of the Grub menu.lst file


If other OS options are not shown in boot menu: 
```
$ sudo update-grub 
```
or
You can manually edit the menu.lst file:
```
$ sudo gedit /boot/grub/menu.lst 
```

You can make up the title to be whatever you want:
title Linux XYZ

but you need to find out uuid values, kernel and initrd file path and names.

To find UUID: ```
$ sudo blkid 
```
To find vmlinuz and initrd file path and names:
Boot from LiveCd, Places -> Removable Media -> the distro partition -> boot folder
or 
Boot into the HDD installed Grub, then at Grub command prompt( grub > ),
Then, to find out where the installed linux distros are,
```
grub> find /sbin/init 
```
 (hd0,7) (hd0,11) (hd0,12)
let's go to that partition...
```
grub> root (hd0,12)   
```
To find out vmlinuz path
```
grub> find / 
```
then press TAB to see the hints
eventually, you will get
```
grub> find /boot/vmlinuz-2.6.28-15-generic
```
```
grub> find /boot/initrd.img-2.6.28-15-generic
```


Copy those file path and names into Grub menu.lst!
That's IT! Easy! Enjoy!

---

### Post by efflandt on 2009-10-26
Thanks.  This gave me a clue where to look to add a boot menu entry with acpi=off because my system never has seemed to work properly with acpi enabled (some errors in /var/log/messages and system locks up at times).  And the Ubuntu docs give no info on boot configuration.  I guess they do not want to overwhelm people unfamiliar with the shell.

Although, everything else seems to work great once I figured out that there is no root login or "su -" and you have to use sudo for system things.  I haven't installed Linux for a few years, so I was a bit rusty.

---

