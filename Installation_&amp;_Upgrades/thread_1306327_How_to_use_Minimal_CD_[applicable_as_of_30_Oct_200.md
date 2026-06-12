---
title: "How to use Minimal CD? [applicable as of 30 Oct 2009++]"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by xycris on 2009-10-30
Hi all,

I want to learn on how to use Minimal CD to make an ultra lightweight operating system for it is very inevitable to opt and support the OpenSource projects due to the stability, reliability, and very educating set of communities they provide.

I want to use the Ubuntu Minimal CD and from there build a customised lightweight operating system because the release is always updated with the following features:

-simple and light graphical user interface for:
[INDENT]-desktop management
-file management
-system monitor
-adding/ removing/ updating programs
-date and time
-network manager (LAN/ DSL/ Wireless Broadband/ WiFi Connection)
-bluetooth manager
-network connections (file sharing)
-printer installer/ manager
-volume manager
-log-in/ log-out/ shutdown/ reboot
-has a terminal
-displays hardware resources[/INDENT]

Plus with the following applications installed:

-Firefox
-Thunderbird
-Pidgin
-VLC player
-K3b (not Brasero)
-OpenOffice.org suite
-Dictionary
-Inkscape
-GIMP
-Google's Picasa
-Calculator
-Character Map
-Manage print jobs
-Text Editor
-Java Runtime Environment
-Adobe Flash

I want to conduct this experiment in an old laptop, Acer Travelmate 2430, connecting to the Internet via DSL. Specs as follows:
RAM: 256mb DDR 333MHz
Processor: Intel Celeron at 1.60GHz 400 MHz FSB
Audio Controller: Unknown but Xubuntu 8.04 can use it properly
With: WiFi 802.11b/g, Bluetooth, LAN, Modem, USB, Audio in/ out jacks, USB 2.0, PC Card Slot Type II, VGA out, speakers, DVD/ CD-RW combo

Any help will be very much appreciated. Thank you very much in advance!

---

### Post by xycris on 2009-11-18
I have been searching for an answer to this topic and I got just the right answer here:

[Installing a Minimal Ubuntu Installation with a Minimal Gnome Desktop]("http://linuxuser.se/~lassekongo83/2009/05/installing-a-minimal-ubuntu-installation-with-a-minimal-gnome-desktop/")

---

### Post by sakisds on 2009-11-18
Ive been trying these things in vms some days ago.
One solution is to use xfce without recommends, it will give you a nice and full featured light desktop.
 
Install using the Minimal CD(don't choose anything when asked to install packages) and when you log in for first time type in:
 
```
sudo apt-get install [FONT=Courier New]--no-install-recommends xubuntu-desktop[/FONT]
```
When everythings done, restart your computer(use "sudo shutdown -r now") and at the next boot you will see the login screen. Some of applications you requested(like firefox) won't be installed, but you can install them easily using "Add/Remove Applications".
 
The second one is installing lxde instead of xfce(xubuntu-desktop). Its even more light that lxde, but i am not sure how to use it or how it works. To install this use the following command after installing the minimal CD(still don't choose anything when asked to install packages).
 
```
sudo apt-get install lxde
```
 
Both will work, but lxde may need some work more that xfce.
 
Hope it helped.

---

### Post by xycris on 2009-11-20
hi sakisds,

i am really doing some trial and error removing and installing stuffs. so far, i usually end up with a broken package especially with the new debian lenny.

i will try that as well. thanks.

---

### Post by xycris on 2009-11-30
Hi,

Can anyone help me? I have so far got a totally good and fast and light running system but I have encountered certail limitations.

I have made the following steps to come up with this operating system:
[LIST=1]
[*]Installed through CLI via the alternate install
[*]After installation gave the following commands:
```
sudo apt-get update && apt-get dist-upgrade
```
[*]Then installed a GUI system with the following command:
```
sudo apt-get install xorg lxde firefox synaptic
```
[*]Then installed vlc, openoffice writer, calc, drawing, impress, claws, pidgin, wine through synaptic
[/LIST]

These are the limitations I encountered:

[LIST]
[*]All files are always treated as executable files such as .odt and .mp3 and I need to do a right click and choose "Open with another program" to view/ edit the file
[*]I don't have a trash manager for the system
[/LIST]

---

