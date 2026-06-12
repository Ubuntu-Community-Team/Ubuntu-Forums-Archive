---
title: "Grub boot option for external USB drive?"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by ulgor on 2009-06-05
OK, here is my problem:

I am running Ubuntu 8.10/Vista as dual boot on my Dell XPS, ubuntu being my main OS, Vista for Adobe/games. I am reluctant to install or upgrade to 9.04 because my system is running smoothly and is tailored to my needs after months of tweaking. 

...Now I want to install the new 9.04 to an external USB HDD, so I can try the new version and use the mobile hdd as a portable system, while keeping my current setup. This is what I did:

1. I created a partition on the usb drive, and installed a fresh ubuntu 9.04 with the CD.

2. With my external HDD plugged in, Grub booted up, showing me a list of all my systems, which are Vista+Ubuntu8.10 on my laptop, and 9.04 on the usb drive. Booting into any of them was fine... **with the usb drive connected!**

3. **Without the USB drive**, booting produced GRUB error 21. I guess that grub + mbr where installed to my usb drive, not my laptop hdd, correct?

4. So I booted into 9.04 (usb drive) and ran something like (sda8 is my 8.10 ubuntu partition): 
```
sudo grub
root (hd0,8)
setup(hd0)

```
afaik everything went fine... this restored my grub, which is now pointing to my old system, and I can dual-boot ubuntu 8.10/Vista. BUT: The 9.04 OS on the external hdd does NOT show up anymore, even when I plug it in before booting

5. What can I do to either: 
a) tell my grub to include the usb drive, showing me a 9.04 boot option? (maybe even when the usb drive was not found) 
b) automatically boot from the external HDD when its plugged in, and boot from the local HDD when its not plugged in?

I assume I have to add another 9.04 entry to my old/restored menu.lst now, which will point to my external hdd. When selected, this option will boot from the external usb drive, or just fail when its not plugged in... which is perfectly acceptable for me, as long as the other boot options show up correctly.
Is this correct? What do I have to do?

---

### Post by labinnsw on 2009-06-05
Examine the menu list on the USB stick. Copy the information for the USB System to the menu list on the hard drive. I do not have a USB system so I cannot show you an example.

The menu list can be found at /boot/grub/menu.lst on each system.
You will need administrative privileges to edit it. (sudo gedit or sudo nautilus from a terminal)

For booting, I would set the default boot to the internal hard drive and manually select the USB when it is plugged in.

---

### Post by ulgor on 2009-06-05
wow, that was quick! just post a question before lunch, and the answer will be there when you are finished... thanks labinnsw!!

ok, I just copied the first boot option from the USB's /boot/grub/menu.lst to my local /boot/menu.lst

this is what I copied:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e485ac74-6142-47e5-bdbd-2ed34af215d1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e485ac74-6142-47e5-bdbd-2ed34af215d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```

so now this is one of the boot options for my local, original GRUB ? the important part here is the uuid, right? 

ok, I am going to reboot now

---

### Post by labinnsw on 2009-06-05
Yup, looks good to me.

---

### Post by ulgor on 2009-06-05
ok. the new grub menu entry shows up correctly, but when I select it, grub says: "file not found"

apparently, it is not looking in the right place, because the usb drive is connected (and, as I said, booting from usb has worked before)

looking at the other entries (the old 8.10-ones), I can see the main difference is that they dont specify a uuid, but have a line that says ```
root (hd0,0)
``` 
is this where grub looks for a bootable kernel?

I just added a similar line to my new entry to set the root:
```
root		(hd1,6)
```

so the whole thing looks like this:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd1,6)
uuid		e485ac74-6142-47e5-bdbd-2ed34af215d1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e485ac74-6142-47e5-bdbd-2ed34af215d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```

I am just trying and guessing here, please tell me if this makes sense at all!
rebooting now...

---

### Post by labinnsw on 2009-06-05
If that does not work, attach both menu lists (from the USB and the Internal HDD) and both device maps. This way I can look at them and see what is going wrong. I will be away for 30 to 60 mins but I will be back.

---

### Post by ulgor on 2009-06-05
arg... now grub says: error 21, disk does not exist.

Now, in my 8.10 ubuntu, starting grub as sudo in the terminal and looking for /boot/grub/stage1 like this:
```
sudo grub
find /boot/grub/stage1

```I get the following:
```
(hd0,8)
(hd1,5)
```
so the (hd1,6) entry above is wrong... my fault... (btw: why am I looking for stage1? I read that the procedure mentioned above helps finding what grubs exist.. please dont assume that I know what I am doing ;) )

I still don't know if specifying a root will help grub to find the 9.04 system, but I will try. Just corrected the root from (hd1,6) to (hd1,5), like this:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd1,5)
uuid		e485ac74-6142-47e5-bdbd-2ed34af215d1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e485ac74-6142-47e5-bdbd-2ed34af215d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```

rebooting now, i will report back in a minute...

---

### Post by ulgor on 2009-06-05
woohooh.. its working! I am writing this from my fresh 9.04 system.

So after copying the whole entry, adding the line root(hd1,5) was necessary to tell grub where to look! 

Do i still need the uid-line? Can you tell me which lines are necessary and if there is another way to find out the uuid of a disk (for example, if I want to write a new grub-menu entry "from scratch") ?

---

### Post by labinnsw on 2009-06-05
Decided to come back early. I still cannot be sure what's going wrong without the menu lists and the device maps. You are on the right path though.

---

### Post by labinnsw on 2009-06-05
If it works, leave it.

---

### Post by labinnsw on 2009-06-05
To find the uuid check /etc/fstab

---

