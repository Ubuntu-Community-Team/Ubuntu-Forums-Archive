---
title: "[SOLVED] win xp &amp;amp; ubuntu boot configure"
date: 2008-08-26
forum: General Help
---

### Post by zeromx on 2008-08-26
hi,
I recently installed Ubuntu onto my computer and have windows xp installed also, i currently have 2 hdd's. one for winxp and one for ubuntu.

question; when i boot my computer it loads crub and lists me boot options, i want to know how i can make windows xp my default boot device and ubuntu my 2nd otpion?..

thank you in advance.

---

### Post by fooman on 2008-08-26
you need to edit the /boot/grub/menu.lst file and change xp to the default.  open the file by running this in a terminal:

```
gksudo gedit /boot/grub/menu.lst
```

near the top of the file you will find a section like this:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```

at the bottom of that section,  you need to change the "0" to whatever number represents xp in the list at the bottom of the file.  
now scroll down to bottom of that file and you will see your kernel(s), memtest, and other operating systems listed.  the first selection in the list is your default kernel, and is repesented by zero (0) in the section i showed you above.....count down to xp in the list and change the "0" in that section to whatever number reflects xp.

as an example,  if you have one ubuntu kernel listed, followed by the kernel's recovery mode, followed by memtest and finally xp...then the default ubuntu kernel would be 0,  the recovery mode would be 1,  memtest would be 2 and xp would be 3.  so if you change "default 0" to "default 3",  then xp will be the default boot selection when you start your computer.  that is only an example,  you will need to look at your menu.lst file and find (count down from zero) xp on the list,  then change the default number to match.

hope that makes some sense and helps a little.

---

### Post by zeromx on 2008-08-26
ok,
i run the command in terminal and it loads menu.lst and this code below is taken from that file; so correct me if im wrong but do i change the (hd1,0) ??? on each of the boot lines. if would be great if you would work the code below and show me hows it done, thanks in advance.. 


> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8dc04a05-4359-49bc-9ff4-ba46292b54cd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8dc04a05-4359-49bc-9ff4-ba46292b54cd ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by mssever on 2008-08-26
> **fooman said:**
> you need to edit the /boot/grub/menu.lst file and change xp to the default.  open the file by running this in a terminal:
You also need to set updatedefaultentry to true. Otherwise, Windows will no longer be the default the next time a kernel update comes along.

---

### Post by mssever on 2008-08-26
> **zeromx said:**
> so correct me if im wrong but do i change the (hd1,0) ??? on each of the boot lines.
Don't touch that. You shouldn't touch any of the lines you quoted.

---

### Post by fooman on 2008-08-26
looking at that code, i see 5 entries listed.  starting with zero and counting down makes xp "4"

so if you edit the top section of that file (like i showed above) from default   0 to default   4,  then xp should boot when you restart the computer.

---

### Post by fooman on 2008-08-26
change this:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		[COLOR="Red"]0[/COLOR]
```

to this:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		[COLOR="Red"]4[/COLOR]
```

---

### Post by zeromx on 2008-08-26
Thanks alot everyone, everyone been great help espically "fooman"...:KS

---

