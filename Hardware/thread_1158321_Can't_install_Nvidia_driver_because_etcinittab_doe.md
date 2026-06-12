---
title: "Can't install Nvidia driver because /etc/inittab doesn't exist..."
date: 2009-05-13
forum: Hardware
---

### Post by nogoodreason on 2009-05-13
Hi guys.  I'm new to Linux, so please speak slowly. ;)

I'm trying to install the latest Nvidia drivers for my 8800GTS 512mb on Jaunty Jackalope x64.

Following the instruction on the website (which was difficult enough, as there was a typo on the page) led me to a message saying I need to disable the X Server before installing the drivers.  After some searching, I learnt that I need to edit a line in the file **/etc/inittab** in order to let me do this.

Problem is: there's no such file, and my attempts to create it wouldn't work because I don't have permission to add a file to that folder.  (And I don't know the root command to copy and paste a file from one location to another, so I can't try just typing 'sudo')

I'm sure a lot of people must have this hassle when installing their nvidia drivers.  Any pointers would be very much appreciated as I'm stumped!

---

### Post by bearslumber on 2009-05-13
You can install them through synaptec package manager.

Search for Nvidia. There are many Nvidia packages. 

See attached screenshot.

Cheers

Lucas

---

