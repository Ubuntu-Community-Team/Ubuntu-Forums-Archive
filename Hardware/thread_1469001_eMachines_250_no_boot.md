---
title: "eMachines 250 no boot"
date: 2010-05-01
forum: Hardware
---

### Post by gt24 on 2010-05-01
Installed Ubuntu 10.04 on a eMachines 250 laptop using Wubi.  Laptop did reboot and start the installer and complete installation.  Laptop was not able to boot Ubuntu after that, no splash screen.  Was able to hit Ctrl Alt F7 to go to see launch messages but it crashed really early on, no idea why.

I took a picture, but it wasn't good (the edges of the screen were cut off).  If you need more details, I can collect it.

However, as far as I'm aware, Ubuntu 10.04 does not work on this laptop at all.  In 9.10 it at least worked with no wireless support.

Any ideas how to proceed?

---

### Post by friendwilder on 2010-05-16
The same here! Using a usb drive UNE works fine, but after installing it, shows the GRUB and selecting Ubuntu 10, the screen shows a black screen and a cursor blinking.

---

### Post by garvinrick4 on 2010-05-16
If one the Forums Staff Members can stick a WUBI on this, I am sure he will get more action on his thread. As I understand there is testing still going on in WUBI for Lucid.

---

### Post by friendwilder on 2010-05-24
After installing Ubuntu for 32 bits, I left the usb connected to the usb port, that was sufficient for ubuntu to run. 
If I leave the usb connected to the usb port, Ubuntu starts, but if not, after selecting ubuntu in the GRUB, ubuntu does not start.

---

### Post by gt24 on 2010-05-25
Thanks for the eventual replies!

I wasn't sure it would have been a Wubi specific issue thus why I labeled it Ubuntu.  The only testing I can do on my 250 is a Wubi install, I will not format my netbook.  However, if I do learn anything more then I will post it.

As for the last post (which was a bit confusing), if I have some time then I can try a USB wireless mouse and a jump drive in the USB ports (there are 3, but I will likely only try one).  I don't think it will do anything but you never know.

---

### Post by 144 on 2010-06-09
This is an ACPI problem.  Re-install and, when you boot into Ubuntu for the first time, hit ESC when prompted and select 'ACPI Workarounds'.  Then all will be well.  Once Ubuntu is running, you'll need to activate the Broadcomm restricted drivers if you want wireless.

---

### Post by gt24 on 2010-06-13
Thanks!  That worked!

Now I have to figure out why my display gets corrupted when switching between terminals.  I can switch to a terminal and when I hit F7 to come back to the GUI it is all messed up.  If I try to (feeling my way through the messed up GUI) enable desktop graphical effects then the distortion goes away (and it says it cannot enable effects, but it cannot enable effects normally anyways).  Still, it would be nice if the desktop doesn't distort.

Might have to make a new thread...

---

