---
title: "cant even start"
date: 2008-09-13
forum: General Help
---

### Post by striker7770 on 2008-09-13
ok, i am really getting frustrated. i need a program that can only run in linux, so i chose ubuntu. so i installed it with a live disk, and it gives me a black screen that i cant move from, if i install it and try to load it from my hard drive, i get the busybox screen. will someone tell me if there is an easier way, or a better way to install unbuntu

---

### Post by javaJake on 2008-09-13
Just to clarify, are you not able to install, or did you get it installed and the installed Ubuntu won't boot at all?

Also, what is the model name of the computer are you using?

---

### Post by striker7770 on 2008-09-13
its kind of complicated, when i tried to install ubuntu as a program on windows with a flash drive, i was up to the part where i could partition the disk, but it said i didn't have enough space, even though i had 30 gigs open. so i went to wubi and it was able to install it, but when i select ubuntu from the os chooser when i set up, it goes to the busybox command prompt thingy, so i finally made a live cd and tried to install that way, but i cant even get to the install screen, it gives me a blank screen that no matter what i do, wont take me out of it. 
my computer is a gateway c-140Xl
1.66 ghz
ati radeon 2300 Hd
101 gigs
thats all i can think of right now

---

### Post by javaJake on 2008-09-13
OK, the first thing that pops into my head here is that the flash drive boot isn't working. Windows finds the flash drive and boots it fine, but when Ubuntu starts up and tries to find itself to load drivers and the graphical interface, it cannot, and so it freaks out and drops you into a busybox.

Describe the blank screen, though. What exactly do you see up to the point where you get the blank screen?

If you're trying to install a mobile version of Ubuntu onto a flash drive, I recommend following one of these guides:

[LIST]
[*]**Non-persistent installation**: changes made are deleted on reboot, easy to do: [http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)
[*]**Persistent installation**: saves changes, harder to do: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/)
[*]**"Real" installation**: Acts just like a normal install, easy to do, requires USB boot in BIOS however: [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)
[/LIST]

---

