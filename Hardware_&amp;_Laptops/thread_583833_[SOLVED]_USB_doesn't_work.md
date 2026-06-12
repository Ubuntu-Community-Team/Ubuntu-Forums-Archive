---
title: "[SOLVED] USB doesn't work"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by gr3gg0r on 2007-10-20
I'm on a dv6449us hp laptop.  My USB ports work fine in Gusty if the device is connected to it when I start the computer.  If the device isn't connected or i disconnect and reconnect it, it won't ever be recognized.  I discovered this by trying to add a USB printer.  I plugged it in and nothing happened and it wasn't detected.  I restarted with it plugged in and it worked fine.  Same thing with a wireless usb mouse.  Help?

---

### Post by Ayuthia on 2007-10-20
You might want to go to the terminal and check dmesg.  If you are booting with noapic, it might be what is causing it.  If you see an issue with IRQ #7, you might try to add noirqdebug and that might fix it.

---

### Post by gr3gg0r on 2007-10-20
I am booting with noacip.  What exactly is acip?  what about acpi?  (i hope i don't sound too clueless with those questions... :[ )  How do I change the command I boot with?  I just did it with the live cd (f6).  How do I customize grub for that matter?

---

### Post by Ayuthia on 2007-10-21
you will need to update /boot/grub/menu.lst to change the kernel parameters.
```
gdesu gedit /boot/grub/menu.lst
```
search for something that looks like ths:
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=blahblahblah ro noapic splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```
Yours should look similar.  You will need to update the kernel line to include noapic noirqdebug or whatever you want to change it to.

From what I understand, HP did not write the BIOS using the standards so some operating systems will have some problems with interrupts such as this one.  Because of this, noapic will disable that part.

---

### Post by gr3gg0r on 2007-10-21
Wonderful, that has fixed the problem :)  I appreciate it.

---

