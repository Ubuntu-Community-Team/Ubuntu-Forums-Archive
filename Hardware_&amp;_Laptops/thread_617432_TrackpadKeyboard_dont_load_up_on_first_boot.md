---
title: "Trackpad/Keyboard dont load up on first boot"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by abhitux on 2007-11-19
I am facing a weird problem. I am using Lenovo Y500 series laptop (in India). When I do a first boot up, the trackpad and the keyboard are not functional. I have to use my USB mouse to make the mouse pointer work. However, after I reboot again by using the USB mouse, the trackpad and the keyboard work just fine. This is the problem that was there in Feisty but Gutsy has not solved it so far. Any workaround for this?

---

### Post by aashay on 2007-11-27
Same problem here:
[http://ubuntuforums.org/showthread.php?t=622698](http://ubuntuforums.org/showthread.php?t=622698)
Nobody willing to help. I've found adding acpi=off to the kernel parameters (in grub) works. But the power mgt stuff (battery, freq scaling etc) doesnt work. PM me if you find anything, This is really irritating the hell out of me

---

### Post by rmsrohan on 2007-12-23
had the same prob but after lots of googlin found that adding 

locale=fr_FR i8042.reset to your kernel line solves the problem with no error on sound or others


eg: 

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.22-14-generic ro quiet splash locale=fr_FR i8042.reset
initrd /boot/initrd.img-2.6.22-14-generic
quiet

---

### Post by aashay on 2008-01-21
That solved the problem!!! I was searching for a solution for month now! Thanks rmsrohan

---

