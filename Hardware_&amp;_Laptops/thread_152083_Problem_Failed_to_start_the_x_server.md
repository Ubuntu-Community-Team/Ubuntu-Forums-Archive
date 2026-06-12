---
title: "Problem: Failed to start the x server"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by antd on 2006-03-29
Can somebody please help me? I've just installed ubuntu 5.10 on a clean install on my hdd.

I've installed it without errors. When it boots and I login I get the following message:

"Failed to start X server (your GUI). It is likely you have not set it up correctly..." I click "yes" to see server output ->

Server Output: 
X Windows system version 6.8.2 (Ubuntu 6.8.2-77 20051010174619
[email]root@crested.warthogs.hbd.com[/email]
X protocol version 11, revision 0, release 6.8.2
Build operating system: linux 2.6.8.1 x86_64 [ELF]
Current OS: Linux ubuntu 2.6.12-9-amd64-generic #1 Mon oct 10 
skipping: /usr/x11r6/lib/modules/extensions/libGlcore.a:_debug_clip.o: No symbols found
(EE) no devices detected.
Fatal server error:
no screens found






It then says "The x server is now disabled. Restart GDM when it is configured correctly". And then I'm stuck at command line. I don't wanna go back to windows =P

My hardware-
Graphics card:- GeForce 6110 Nvidia chipset

Any help to get this fixed will be much appreciated.

---

### Post by Sutekh on 2006-03-29
Try using this command
```
sudo dpkg-reconfigure xserver-xorg
```
 - when prompted for a password, use your users password.  The characters of the password won't appear on the screen, but trust me it is typing them.

 - this command will reconfigure the X server (the GUI),  you will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor.  If you don't know what you should answer to these questions go with the default/suggested ones.

 - the important step is when you are asked to choose the video card driver for the X server choose **nv**

 - once you are done use this command
```
sudo /etc/init.d/gdm resart
```
 - this will restart the GNOME Display Manager, and start the GUI.

 - If this all works out then you can consider installing better NVIDIA drivers to take advantage of you card.  You can read all about it here

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by nazish on 2006-03-29
First let us graphical boot your computer.....
1.)First backup your copy of xorg.conf
todo this run the fllowing command
sudo cp /etc/xorg.cong /etc/xorg_backup.conf

2.)
after you login enter the following command
sudo vi /etc/X11/xorg.conf
after the file opens find the line which contains someting like Driver(this line contains a string specifying the manufacturer of your card)  change it to "vesa" by changing it to vesa we mean that xorg should load the generic drivers,

3.)
Run the command startx

in case of any fault just replace your old xorg.conf with the following command

sudo mv /etc/xorg_backup.conf /etc/xorg.conf

---

### Post by antd on 2006-03-29
thanks for the support. i'll do this now.

---

