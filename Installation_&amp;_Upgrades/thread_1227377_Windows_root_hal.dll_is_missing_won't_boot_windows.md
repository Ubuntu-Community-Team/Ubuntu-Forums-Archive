---
title: "Windows root hal.dll is missing won't boot windows"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by JRGNH on 2009-07-30
Hi, I put windows on my computer after I had Ubuntu on it for years. It windows XP Home. I installed Ubuntu 9.04 awhile back and when I went to get into Windows last night. It came up with the Message telling me that hal.dll is missing.  

  I have been searching all the forums, I now know what hal.dll is and what it is for. 

  I also have checked Menu.lst for grub and everything seems to be in order.
Also went and took a look at Boot.ini And everything seems perfect. 

Boot.ini 
-------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition"  /noexecute=optin /fastdetect
--------------------------------------------------------------------------


Sudo Fdisk -lu
--------------------------------------------------------------------------
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   163943324    81971631    5  Extended
/dev/sda3   *   163943325   234420479    35238577+   7  HPFS/NTFS
/dev/sda5             126   157179959    78589917   83  Linux
/dev/sda6       157180023   163943324     3381651   82  Linux swap / Solaris
-------------------------------------------------------------------------


And finally GRUB's Menu.lst
-------------------------------------------------------------------------
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------

   What could the problem be!!!! I even went to the extent of replacing the hal.dll in the system32 File. didn't work so I put it back the way it was. Any help would be greatly appreciated. thank you.

---

### Post by Mark Phelps on 2009-07-31
Here's a link to some info:

[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm]("http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm")

But, if your boot.ini is damaged as well, it could be that your install didn't complete properly.

---

### Post by JRGNH on 2009-08-04
Oddly enough, I just inserted the windows CD. I expected it to destroy grub and had a backup made of Menu.lst, Just incase it did. Instead I went through the regular repair of windows and it left grub alone and repaired everything without any issues and now Windows is working as well as can be expected. I will say one thing about having a windows machine. You always have something to work on or fix. And once you fix that, another problem will come up so you can rest assure that you will always be busy. :D

---

