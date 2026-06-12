---
title: "Logitech G110 keyboard not working in grub"
date: 2011-09-14
forum: Hardware
---

### Post by area5x1 on 2011-09-14
I just bought a Logitech G110 keyboard and I really like it but the keyboard just won't work at all in grub! It works perfect when either Linux or Windows is loaded, but during the OS selection it just refuses to work. The keyboard even works fine in the BIOS.

I already have Legacy USB Support checked in the BIOS. The strange thing is though that my $5 generic keyboard I bought at Target works fine. Right now I"m using it as a workaround, but it's really annoying having to unplug and replug in keyboards during startup.

I think the problem is that my motherboard is detecting my G110 keyboard as 2 keyboards for some reason. When I check the list of connected USB devices in the BIOS, I see "2 keyboards, 1 mouse, etc" which is definitely odd because I only have 1 keyboard connected. I'm not sure if this conflicts with grub or not.

Any ideas?

---

### Post by area5x1 on 2011-09-15
Any ideas?

---

### Post by orthopod on 2012-07-09
Well - I have the same problem
ASUS p8z77V,  i5 processor

keyboard x 2 detected during boot up, and works fine in BIOS , but refuses to work during GRUB.   Works fine after GRUB autoloads into UBUNTU/MINT


USB legacy is enable in BIOS

---

### Post by m3lkor81 on 2012-11-24
Strange thing!I've the same problem here with my laptop. When i connect the keyboard i can't move the cursor to select os. Not only yhe g110 will not work but the laptop's keyboard too seems unresponsive. I can just select the first element of grub's list.
After boot all seems to work just fine... I haven't tryed to make a clean install, but i don't think that may be a solution :\

---

### Post by ryo80 on 2013-06-08
To get the g110 working i set Usb Operational Mode from Full Speed to Full/Low speed in my bios. It seems to be ok with grub only when working connected on usb 1.0/1.1 mode, only usb 2.0 mode on boot seems to fail.

---

