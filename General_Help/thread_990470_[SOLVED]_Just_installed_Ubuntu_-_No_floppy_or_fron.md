---
title: "[SOLVED] Just installed Ubuntu - No floppy or front USB"
date: 2008-11-22
forum: General Help
---

### Post by dstein on 2008-11-22
Hi. I just installed Ubuntu 8.10 64-bit on a new computer. I accidentally did not have my front USB ports plugged into the motherboard when I installed. After plugging them in, they are still are not usable in Ubuntu. However, my BIOS recognizes an external hard drive when it is plugged into one of the ports. How can I enable these ports in Ubuntu?

Also, Ubuntu is not mounting my floppy drive. You may be wondering why I have a floppy drive, and so am I. Although I don't need this drive, it would be interesting to know why it is not recognized in Ubuntu, and how I can enable it.

Thanks.

---

### Post by plucky on 2008-11-23
> Also, Ubuntu is not mounting my floppy drive. You may be wondering why I have a floppy drive, and so am I. Although I don't need this drive, it would be interesting to know why it is not recognized in Ubuntu, and how I can enable it.


Try **Applications > Accessories > Terminal** and input this command ```
sudo modprobe floppy
```.This will load the driver for the floppy.
If that works,then to make sure the driver is loaded at every boot you have to edit a file with the command ```
gksudo gedit /etc/modules
``` and add the word **floppy** on a separate line.

> Hi. I just installed Ubuntu 8.10 64-bit on a new computer. I accidentally did not have my front USB ports plugged into the motherboard when I installed. After plugging them in, they are still are not usable in Ubuntu. However, my BIOS recognizes an external hard drive when it is plugged into one of the ports. How can I enable these ports in Ubuntu?

I am very surprised the USB ports don't work.From a terminal ```
lsusb
``` and see what is there.Then plug something into the front ports and run the same command.See if the output changes.


Welcome to Ubuntu

Good Luck

---

### Post by dstein on 2008-11-23
Thanks. The modprobe program worked. I'll add that to /etc/modules. I actually already tried lsusb, which I should have mentioned in my initial post. No success. Any other ideas?

---

### Post by dstein on 2008-12-02
The front USB ports were not plugged inproperly, I had the pins shifted by accident. I'm not sure how it recognized the hard drive though (maybe it didn't and I am just imagining...)

---

