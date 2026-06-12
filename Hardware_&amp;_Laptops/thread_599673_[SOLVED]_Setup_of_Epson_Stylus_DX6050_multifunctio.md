---
title: "[SOLVED] Setup of Epson Stylus DX6050 multifunctional"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by cirorodrigues on 2007-11-01
**[SIZE="4"]This is a howto about Epson Stylus DX6050 multifunctional setup.[/SIZE]**

**one recommendation**

I've bought this device some months ago and I'm very satisfied. I do recommend it for use with Ubuntu (and Linux in general) as it has many features that I consider interesting to a Linux user. Many printers and multifunctionals are designed to run under Windows and require monitoring software to indicates low level of ink, etc. These softwares normally have only Windows versions.:mad:
This one is a quite stand alone equipment, having a small control panel with a lcd and buttons that allow us to do some tasks like monitor level of ink, change print quality, align, clean heads up and change cartridges without need to any software. Of course, there's Windows software for it, but who needs it?  :)
My other printer was an Epson Stylus Color 580, which prints very well under Linux. But when you either run out of ink or have any other trouble you must guess what's happening as there is not a single led to provide information, and the printer suddenly stops working. I've been using some additional (and cumbersome) software as Stylus Toolbox or MTink, which needs to run under root permissions, but it was not a good experience for me, and I think it's not easy for beginners.
Well, this was just to help some people looking for a multifunctional that can run under Ubuntu.

**Now the facts**

I installed it first on Feisty and after a fresh install of Gutsy I followed it and it worked flawlessly.
I didn't try with other Epson multifunctionals, but as the process described below was based on several posts regarding others Epson models, I guess it should work for others also. I noted the points were I needed to adjust, so you can do your own adjustments.
[B]
First step - printing[/B]

In Feisty, I needed to manually add a new printer. Gutsy did it automatically when I turned it on.:)
So, you should add a new printer, manually or automatically. Name it as you wish to.

Just check the driver's setting:
[INDENT]Manufacturer: Epson
Model: Stylus DX4800   --- NOTE: I didn't find DX6050. Feisty and Gutsy both suggest DX4800 and it works well.
Driver: High Quality Image (Gutenprint Cups) Expert
Conexion: local / detected printer Epson Stylus DX6000 USB#1[/INDENT]

After that, I've printed a test page successfully.

**Second step - scanner**

Even the printing was fine at first shot, when opening Sane it insists to look for my webcam, what goes directly to an error, and no scanner at all. So I needed to adjust something here. Thanks to all guys that have posted in this forum and who give me clues to work out!

run in a terminal:
[INDENT]lsusb | grep Epson[/INDENT]
look for a line showing something like:
[INDENT]BUS 005 Device 003: ID 04b8:082e  Seiko Epson Corp.[/INDENT]
The info above can be different depending on your device. Important information is the ID. Keep the numbers 04b8:082e (or whatelse you get here).
Edit the following file, as root (using sudo):
[INDENT]/etc/udev/rules.d/45-libsane.rules[/INDENT]
Add the following line (it's a single one):
[INDENT]SYSFS{idVendor}=="04b8",SYSFS{idProduct}=="082e",MODE="664",GROUP="scanner"[/INDENT]
Note that the idVendor and idProduct are the numbers printed by lsusb.
Save and close the file.
Edit the following file, as root (using sudo):
[INDENT]/etc/sane.d/epson.conf[/INDENT]
Add the following line (it's a single one):
[INDENT]usb 0x04b8 0x082e[/INDENT]
Again, these are the same numbers.
Save and close the file.
Now, test the scanner typing "scanimage -L" in terminal as normal user. I supposed it'll do nothing. So, test again using "sudo". It should now identify the scanner device as Epson.
If the step above works as root, it's a permission issue. Do the following:
[INDENT]sudo chmod a+w /dev/bus/usb/005/003[/INDENT]
where 005 and 003 refers to BUS and DEVICE identified by lsusb, respectively.
Reboot the system.
Now you should be able to start Sane directly by Gnome menus.
I still get an error after close Sane, and I know that's related to permissions also, but this is not blocking the usage. I suppose it's some file Sane is trying to write on a folder I have no rights, but I had no time yet to look and fix it.

---

### Post by doclongopc on 2007-11-06
Marvelous..
It works perfectly also with dx 5050.
In my laptop I edit epkowa.conf instead of epson.conf, that works else.
Many thanks Ciro.

ps:sorry for errors

---

### Post by nautica19 on 2008-01-27
thanks

---

### Post by cirorodrigues on 2008-06-11
> **cirorodrigues said:**
> 

I still get an error after close Sane, and I know that's related to permissions also, but this is not blocking the usage. I suppose it's some file Sane is trying to write on a folder I have no rights, but I had no time yet to look and fix it.

The cause for this problem was a permission problem. During the installation and test, the first successful scanning was done under root (sudo) and Sane created a ".sane" folder in my home folder with root as owner. I eliminated it and Sane automatically created a new one with correct permissions.

By the way, it works perfectly with Ubuntu 8.04 Hardy Heron. I followed this how-to step by step with no problems.

---

