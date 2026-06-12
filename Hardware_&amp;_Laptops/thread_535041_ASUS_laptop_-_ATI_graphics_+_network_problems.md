---
title: "ASUS laptop - ATI graphics + network problems"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by occhiso on 2007-08-26
Hi,

I am new to Ubuntu, and wanted to dual boot with XP.
I have been using this tutorial:
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

**Problems:**
[LIST]
[*] I have an ATI x1700
[*] I wanted to dual boot with an existing XP
[*] system rescue CD (another distro) wont startx (ati problem) so instead I use PC-linux, which will. Then my wireless get configured automatically, i use apt-get and download gparted. This is used in the tutorial above
[*] cannot access my network, or the internet from ubuntu
[/LIST]

**What ive done so far:**
[LIST]
[*] I have windows XP installed, have used PClinux with gparted to partition my drive into 4 partitions, windows, linux, swap and a fat32 to share data between windows and linux
[*] run the text based installer for ubuntu
[*] edited my windows boot.ini to give me the option to boot windows or ubuntu - without grub (followed the tutorial)
[/LIST]

**My current problem:**
As I have an ati card (x1700), I had problems installing ubuntu from the live cd, so instead, I used the ubuntu alternative ISO and installed it with the text mode installer (as per the advice from this forum).
I beleive it installed fine, and I was hoping to be able to load a terminal and get the xorg-driver-fglrx from apt-get, but I can seem to get onto my network.

When I boot I am given the option to boot windows or ubuntu, and when I boot ubuntu, I get a black screen with a '_' character flashing. I think this is because it is lacking the video card drivers... but it doesnt give me a terminal

Again I booted off the alternative ISO and I have tried setting up my ip address and default gateway using the rescue mode (ifconfig and route add), but i simply cant get on the net to get my drivers.

Im a complete noob at this stuff so any help would be greatly appreciated!

thanks,
occhiso

---

### Post by occhiso on 2007-08-27
Hi,

My problem is fixed!
I had my local help desk solve the problem for me, all I can say about how it was solved is that I needed internet access, and obtained that by installing wireless card drivers, then obtained graphics card (fglrx) using aptitude.

After a bit of configuring, its up and running.

occhiso

---

