---
title: "Ubuntu on HP Pavilion dv6790ej?"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by idodos on 2008-04-17
So the question is, will Ubuntu run on HP Pavilion dv6790ej?
here is some of the hardware on dv6790ej:

Intel Core 2 Duo T9300 2.5 GHz
4096MB (2x2048MB) DDR2
250GB 5400rpm
DVD Writer Double Layer LightScribe
Nvidia GeForce 8400 256MB

Thanks in advance.

---

### Post by nicedude on 2008-04-17
I am sure it will idodos as it will run on almost any modern PC on earth but the trick is support for your different hardware devices in your laptop, some will be easier to get going than others. The CPU, RAM, DVD burner & Hard Drive will all be supported automatically. Your Nvidia graphics adapter takes installing a driver for it to get 3D effects and good resolution but it isn't hard and you can get help here in the forums. Wireless might be tricky to get to work properly depending on what wifi chipset your laptop uses. Webcam might take a little fiddling with and so might sound drivers. But more than likely everything will work, you just will have a learning curve as you jump into it. I woud recomend you download a Live Install Ubuntu CD image and burn it to disk then just boot your laptop with it .it wont change your hard drive at all it just loads the system into ram but is full version of ubuntu and will give you a good chance to see if you like it without having to risk anything but a 25 cent blank CD. Just remember though that since a CD/DVD drive is no where near as fast as a hard drive it will take like 3-4 times as long to boot up Live as it would if it were installed on your PC'S harddrive. Im jealous of your 4GB ram laptop as mine only has 2GB ram but I do have a nvidia 8400m graphics card  at least :-)      


Well I hope you take my advice and try booting a live CD and try it out, once you get it all set up its awesome and has more eye candy and looks better than Vista Ultimate. Well hope this helps you ditch Microsoft's Junk OS

---

### Post by BOOBOOJS on 2008-04-17
Try it out :)

I have an dv9008nr and Iit works with some tweaks!

HP has a BIOS bug that causes most Linux distros to lock up on boot.
To avoid it add "noapic noirqdebug" without the quotes to your kernel line.
This will tell Linux to work around the problem.

If installing hit F6 and type it in at the end of the line and hit enter
If you got through the install the hit e at the GRUB screen, select the kernel you wish to boot (usually the one at the top), hit e again, type it in and hit b to boot.
After your system boots open a terminal window (in accessories) and type "sudo gedit /boot/grub/menu.list"
Append "noapic noirqdebug" without the quotes to the end of all of the lines beginning with initrd=

If you have a different issue search the forum or provide some additional info and someone will probably have the awnser.
If you are shopping for a new laptop HPs mostly work with the above fix, but it might be wise to google for a Hardware Compatablility List for Ubuntu

---

