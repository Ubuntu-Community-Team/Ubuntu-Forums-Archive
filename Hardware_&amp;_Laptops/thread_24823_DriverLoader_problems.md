---
title: "DriverLoader problems"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by aphonik on 2005-04-08
Hey,
Im trying to install my D-Link DWL-G650+ drivers using DriverLoaader after repeatedly failed attempts using NDISwrapper. The trouble, when it goes into the browser and asks me to enter "root as the username and the corresponding password". So i type in root as the username, and my password as the password but it doesnt let me in! Is there a predefined password for the root account that I can use?

Aphonik

---

### Post by az on 2005-04-08
You should complain to the people who sold you the app.

---

### Post by lao_V on 2005-04-08
[QUOTE=aphonik]Hey,
Im trying to install my D-Link DWL-G650+ drivers using DriverLoaader after repeatedly failed attempts using NDISwrapper. The trouble, when it goes into the browser and asks me to enter "root as the username and the corresponding password". So i type in root as the username, and my password as the password but it doesnt let me in! Is there a predefined password for the root account that I can use?

Aphonik[/QUOTE]

First, you need to enable the root in terminal:

 ```
sudo passwd root
``` 

Then enter your password and the new root password twice

Once that is done you can open up the driverloader app in browser and enter root for username and the new password you entered above.

Let me know if you have any further problems with DriverLoader

---

### Post by aphonik on 2005-04-08
Thank, I can now get into the browser, but because I am not connected to the internet I cannot download any of the packages. Is there anyway to continue with it without connecting my computer to the net?

Aphonik

---

### Post by waxy41 on 2005-04-27
Hi, I was trying to install driverloader, I got past the root password problem, but, once the driverloader program starts, it looks for packages, and tells me there is none compatible for my system.  It suggested installing gcc, kernel-source and kernel-headers, I have done this, and still it doesnt want to work...  Any help would be greatly appreciated!

---

### Post by lao_V on 2005-04-27
Instead of installing through the installer, use the [deb package]("http://www.linuxant.com/driverloader/wlan/full/archive/driverloader-2.27/driverloader_2.27_i386.deb"), making sure you have installed build-essential and linux-headers for your system

---

### Post by jbraum on 2005-10-11
Does anyone have a step by step for getting driverloader to work?  

I've tried dpkg -i driverloader_2.29_k2.6.10_5_386_ubuntu_i386.deb 

and get 
cannot access archive: No such file or directory
Errors were encountered while processing:
 driverloader_2.29_k2.6.10_5_386_ubuntu_i386.deb

Any help would be great.

---

### Post by MilestoneIII on 2005-10-22
Um, I've been having problems with the new 2.6.12 kernel and my Dell 5150 w/Driverloader. But the problem here sounds like it's with the kernel sources, and gcc. I'm not a guru, so this may or may not be it, but in order to compile driverloader into the kernel, try using apt-get or synaptics to get the kernel-tree, linux-headers, and the kernel sources. with all of those, plus gcc 3.3 or 3.4, it should work. I followed  the ubuntuguide.org for the build-essentials and got my nvidia grafix working before the wireless. Anyway, hope it helps! Try using Synaptic to search for anything about the kernel tree, sources, and headers. Make sure they're for your arch and correspond to the kernel you wish to use :) Good luck!

---

