---
title: "Please help! Webcam stopped working"
date: 2008-06-23
forum: Hardware
---

### Post by ahbart on 2008-06-23
Hi,
After a week holiday I updated my Ubuntu hardy install including a kernel update to 2.6.24-19 (X86_64). Before that my webcam, a Logitech Quickcam Messenger (ID 046d:08da Logitech, Inc. QuickCam Messanger) was working well. I used Camorama, Skype and Cheese. All doing well.
After the update The Cam stopped working. The LED light is constantly on.
Camorama says: Could not connect to /dev/video0 etc. I tried /dev/video1 and 2 also because of my tv-card.

I tried to install gspcav1-20071224 from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
This doesn't work either. I found out that when I place 'blacklist gspca' in /etc/modprobe.d/blacklist and than reboot and 'sudo modprobe gspca' my cam is working!
But it is very irritating to do this everytime! And My wife cannot do this when I'm not at home.
I really do not understand what is happening here! Can anybody help me with this please? Is this a bug in any package?

---

### Post by silvanus2005 on 2008-06-23
Normally you still have the old ubuntu kernel on your hard drive. You can log into Ubuntu using the old kernel (in which your webcamera worked) and you can uninstall the last kernel, and everything should be fine. To uninstal you last kernel you can go to System-Administration-Synaptic Package Manager and search there for linux-image. Mark the last kernel for uninstallation, and that`s it.

---

### Post by ahbart on 2008-06-23
Thanks for your answer. 
I just tried the last grub entry 2.6.24-18 but it did not solve my problem. If the kernel update is not the source of my problem, what else could go wrong then?

---

### Post by silvanus2005 on 2008-06-24
In this case I do not know. Maybe you should search in others sections of the forum, such as Multimedia. Maybe you will find somwthing useful here
[http://ubuntuforums.org/showthread.php?t=803140&highlight=Logitech+Quickcam](http://ubuntuforums.org/showthread.php?t=803140&highlight=Logitech+Quickcam)

---

