---
title: "X can't start - graphics card not detected?"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by kasakka on 2006-03-12
I've had this problem on this machine since I first tried Ubuntu from the LiveCD. It works just fine on other machines but not on this one. It always seems to get stuck (5.10) or go back to console (Dapper flight 5). The logs shown seem to have something like ATI PCI Mach64 1:0:0 not detected or something like that.

The weird thing is that I can get it to run fine when I run the LiveCD image via VMWare Player in Windows XP. Obviously it's pretty slow but at least it works. Any ideas on how to get it to run without VMWare player?

My system specs:

Athlon64 3000+ processor
Asus A8N-E (nForce4) motherboard
1 GB DDR
Benq DW1640 DVDRW drive
Samsung 250GB SATA2 hard disk drive
Radeon X800XL PCI-E graphics card
Soundblaster X-Fi XtremeMusic soundcard
Viewsonic VP201 TFT monitor

---

### Post by kasakka on 2006-03-13
Bump. No ideas on how to fix it?

---

### Post by encompass on 2006-03-13
does the live CD work on the system with out useing the vmware... in other words reboot with the cd in and does it work?

---

### Post by Teroedni on 2006-03-13
Use the dapper one, and change your xorg file



in Xorg change driver "xxx" to
driver "radeon"
Does that work?

---

### Post by kasakka on 2006-03-17
[QUOTE=Teroedni]Use the dapper one, and change your xorg file

in Xorg change driver "xxx" to
driver "radeon"
Does that work?[/QUOTE]

Yes, now I can get to the Ubuntu desktop and use it normally, but the only problems are:

1) Only available resolution is 640x480 with some weird -23145 (random number) refresh rate. My monitor is properly identified in xorg.conf and all resolutions are shown but not so when Gnome is started. What can I do?

2) Random blinking crap on the desktop in Windows the display settings had a "reduce DVI frequency" and "use alternate DVI something" options that fixed it. However, I didn't notice this on my previous computer using the same monitor and also an ATI graphics card so I'm guessing it's just some configuration thing.

---

### Post by kasakka on 2006-03-22
Bump. Any help?

---

### Post by Teroedni on 2006-03-23
Post your xorg log here
```
sudo gedit /var/log/Xorg.0.log
```

It probaly use 3 pages. Thats okay :)

I will see what i can spot:)

-----------------------------------------------------

But if you want 3D the fglrx driver is your only chance.
Have you tried installing the latest Ati Propiery driver for linux?
I think the latest have support for your card:)




Hope this helps

---

### Post by real_kastor on 2006-04-23
Hi,

I've a x800xl based card too and my advice is to use the vesa driver instead of the radeon or ati drivers. With this one, you can use all resolutions and color settings your card and display/monitor supports. The fglrx module from ati can do this too.

Greetings, Kastor

---

