---
title: "Usb mouse not working after start up"
date: 2009-11-22
forum: Hardware
---

### Post by Raufio on 2009-11-22
my usb mouse doesn't work if i plug it in after i start my laptop up. It does work if i have it plugged in when i boot up. lsusb shows it and dmesg shows:

[ 2158.976049] usb 2-6: new low speed USB device using ohci_hcd and address 3
[ 2159.188285] usb 2-6: configuration #1 chosen from 1 choice

After i boot up with the mouse in the usb i can unplug it and plug it back in and it still works. I was just wondering if there is something i can do to make it work after i start up, or do i have to restart my computer every time i forget to plug the mouse in?

---

### Post by kr0n1x on 2009-11-28
The opposite happens to my computer.
I boot up my Ubuntu 9.10, and the mouse doesn't work (in the login screen and after the login either).
I'm forced to plug out and plug it in again to make it working correctly.

What could be the reason?

I use a Logitech MX 310, probably I'm still using evdev driver (I'm upgrading Ubuntu since version 7.04 probably :p or a bit later, no fresh installations since a lot of time)

---

### Post by jojodrum3 on 2010-01-09
I've got the same issue as kr0n1x. When I boot with the mouse plugged in, only my trackpad works and I have to unplug and replug the mouse for it to function. I've got 9.10 on an HPtx2000.

---

### Post by kr0n1x on 2010-01-09
I don't know why, I don't have that problem anymore. It got fixed automatically :lolflag:

---

### Post by akshayas1986 on 2010-11-01
Same problem with me too.

---

### Post by rahulr88 on 2010-11-07
same prob here too no sol'ns ???

---

### Post by kolpa on 2011-02-05
Any suggestions on this topic? I have been expriencing this problem on 10.04 (2.6.32-27).

---

### Post by mymiasma on 2011-08-19
I found another solution other than replugging the USB mouse. At boot enter your BIOS setup and look for an Integrated Peripherals section. It's counter intuitive, but worked for me. I disabled the USB mouse support entry. I have no idea why this worked but if you have the same problem give it a try, if it doesn't work you can always reset it by entering the BIOS again and changing it back to enabled.

Also see: [http://www.techmetica.com/howto/ubuntu-postinstallation-problems-and-solutions/]("http://www.techmetica.com/howto/ubuntu-postinstallation-problems-and-solutions/")

---

