---
title: "Lost mouse and touchpad after virtualbox install"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by Oliver Acevedo on 2007-03-11
I'm pretty new to Linux and don't know how to navigate very well in the terminal. So far I've had a fairly good experience with Ubuntu. I'm Dual booting with windows and I was wanting to be able to access Windows without having to reboot. I tried VMware but for some reason that didn't work (I need to use my existing windows and I guess it had authentication issues). Anyways, so I tried to install virtualbox. I downloaded the .deb file and double clicked on it but nothing seemed to happened. I tried again and was convinced nothing happened so I rebooted. I got an error when I tried rebooting, something having to do with the virtualbox dev I think. Anyways, it tried to do an automatic disk check but it was unable to fix it. It asked if I wanted to try doing it manually and I did. There were many devices that were corrupt for some reason and it asked me a ton of questions giving me only one choice of answering "yes". So I answered yes to all of them and it was able to reboot again. Except that now I can boot into linux but I have lost access to my mouse. I can see the cursor but my usb mouse or touchpad does not respond. I'm able to snoop around very limitly with the keyboard and access the files, root terminal and even firefox. But I can't access any other programs because I need the mouse to access "Applications" "Places" and "System". I'm sorry I can't provide too much information. I would like help and if any other information would be helpful to know, please let me know. I've searched the forums but I think my devices were corrupted with the installation of virtualbox and I haven't seen this problem anywhere. Any help would be greatly appreciated. Thank you

Oliver

---

### Post by Oliver Acevedo on 2007-03-12
Thanks anyways for the help. I guess no one decided to reply to my question but that's fine, I figure it out. I found a line of code that aloud me to edit the settings Linux had for the mouse. 

sudo dpkg-reconfigure xserver-xorg

I have no idea what this is or why this worked. I just ran it and messed around with the settings (being careful not to change something I didn't want to change) and then my mouse worked again! This might be a dumb question to ask here cuz I doubt very many people are reading this now but how am I suppose to know that command? There's a ton of commands that have helped me out in the past with wireless troubleshooting and such but where are all these commands? Is there a book out there that has all of these that I can look up and learn so that next time I have a problem I'll know exactly what command to run? Thanks anyways for your help.

---

