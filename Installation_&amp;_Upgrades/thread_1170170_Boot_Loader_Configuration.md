---
title: "Boot Loader Configuration"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by Morphaeus on 2009-05-26
I have a dual boot system with Ubuntu and Windows XP on it. I am pretty new to Ubuntu but I was wondering if it's possible to configure the boot loader to load Windows automatically instead of Ubuntu.

Much appreciated

---

### Post by VastOne on 2009-05-26
> **Morphaeus said:**
> I have a dual boot system with Ubuntu and Windows XP on it. I am pretty new to Ubuntu but I was wondering if it's possible to configure the boot loader to load Windows automatically instead of Ubuntu.

Much appreciated

Sure is...

Get startupmanager from Synaptic Package Manager and it will be self explanatory on how to do it

---

### Post by themusicalduck on 2009-05-26
First install the program startupmanager.

Go to Applications > Accessories > terminal and type

```
sudo apt-get install startupmanager
```

into the terminal.

Once it's installed find the program in System > Administration > StartUp-Manager

On the first tab it lets you choose which OS to startup by default.

---

### Post by Shazaam on 2009-05-26
Do you want to learn a little basic cli (command line interface) usage?
1. Open terminal (Applications>Accessories>Terminal).
2. Type in...
```
gksudo gedit /boot/grub/menu.lst
```
(that's letter el st and the code opens menu.lst for editing), hit enter then type in your user password (you won't see it) and hit enter again.
3. Scroll down to the first kernel entry. Example...
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, memtest86+
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
4. Starting with 0 (zero) count the entries including your Windows entry. The Windows entry should be 3 on a fresh install (0, 1, 2, 3,).
5. Scroll back up to here...
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
and change the default number to the one you want.
6. Press CTRL+S to save, CTRL+W to close or CTRL+Q to quit gedit.
7. Reboot to see if your editing worked. Windows should be highlighted in the grub boot screen and should boot first.

---

### Post by Morphaeus on 2009-05-30
I tried out Startup Manager and it was exactly what I was looking for. I'm just now reading the other responses however, I have not tried them yet. But Startup Manager worked perfectly.

Thank you

---

