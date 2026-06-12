---
title: "Basic command line install of Ubuntu guest: how to install guest additions?"
date: 2008-10-16
forum: General Help
---

### Post by maxxum on 2008-10-16
I have Ubuntu hardy 64 bit as my main OS. I wanted to play with a basic command line install and use icewm to get a feel for it. Maybe in the future I might use it as my main OS if I am comfortable enough. So I installed a command line basic Ubuntu using the alternate CD as a guest in virtualbox. I installed icewm and it is working. I cannot install guest additions. I have the options of mounting the ISO from virtualbox menu but selecting it does nothing. If I do sudo fdisk -l in the guest, it only shows the virtualbox hard drive details. There is nothing mounted in the /media/cdrom or /media/cdrom0.
I have that iso file set to be mounted upon boot of that guest but it is not mounted. How can I install guest additions and get mouse pointer integration and a bigger screen in the guest?

Thanks.

UPDATE: I solved the problem partially by making a directory called iso in /media nad mounting /dev/cdrom manually into it. I had to compile linux headers and was able to get the virtualbox guest additions installed. The window size has gotten bigger but it is still small for me. I want like a 1680x1050 or more size. Increasing the window size and selecting "automatically resize guest" does not work. I fiddled with the /etc/X11/xorg.comf by adding 
Mode "1680x1050" in the Screen  section but X failed on reboot. So I replaced it with the original xorg.conf. So any pointers to that end would be helpful. thanks!

---

