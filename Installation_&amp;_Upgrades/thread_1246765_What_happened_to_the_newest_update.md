---
title: "What happened to the newest update???"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by emeraldgirl08 on 2009-08-22
I have two laptops that have Jaunty on them. I updated both of them the other day. After an update on one of them I got a prompt. It asked if I wanted to keep the current menu.lst or the suggested menu.lst. There were also options to have both side by side etc. I chose to keep the current setting. This produced no new Grub options and does not include the current kernel.

On my other laptop I chose the first option- the suggested menu.lst. This shows a multitude of kernels upon Grub menu- including the latest kernel.

How do I get this expanded menu.lst with latest kernel on the other laptop??? Is there a command in Terminal that will let me do this?

---

### Post by zvacet on 2009-08-22
```
sudo update-grub
```

---

### Post by emeraldgirl08 on 2009-08-22
That didn't work.

Looking at my /Usr/src folder I see the kernel package there. 

This is what my menu.lst looks like:

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7 (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


```

There were the older packages but I saved a copy and for simplicity edited out the older kernels. The newer one ending in -15 is not included in my menu.lst. 

How can I get this menu.lst updated???

---

### Post by emeraldgirl08 on 2009-08-23
bump

---

### Post by mgmiller on 2009-08-23
Since the -15 kernel is not in your menu.list, you are not running it.  Lets try completely removing and reinstalling it.

In synaptic, search for:
 linux-image-2.6.28-15-generic

Right click it and select "Mark for complete removal"

This will also prompt you to remove the other modules for -15 as well.

Let it do it's thing.
Then reinstall the linux-image-2.6.28-15-generic.  This should put all the other packages it needs back in and It should re-prompt you for the menu.list thing again.  This time you know what to do.


Edit:
In fact, after removing it, all you may need to do is rerun Update manager and have it scan for updates.  It should see the new kernel and prompt you to install it.

Don't forget to close synaptic before running update manager, or it won't work.

---

### Post by Shazaam on 2009-08-23
You can add the new kernel manually by editing grub...
1. Open terminal.
2. Enter this...
```
gksudo gedit /boot/grub/menu.lst
```
(that's a lowercase L not a one)
3. Scroll down to the first Ubuntu listing...
```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

```
and right-click copy. Paste it just above the one you just copied.
4. Change ALL of the -14's to -15.
5. Do the same with the "Recovery Mode" entry. You will end up with something like this...
```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic


title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

```
6. Go to "File-Save"
7. Reboot.

---

### Post by emeraldgirl08 on 2009-08-23
Thanks a lot guys :)

My reboot shows Grub with 14 and 15. I checked with System Monitor and it shows that I am running Kernel 15!

Have a good evening!

---

