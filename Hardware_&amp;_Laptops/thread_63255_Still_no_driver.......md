---
title: "Still no driver......???"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-09-07
Hi..
Well its been too long now.
I have tried EVERY tread to get ATI drivers to work.
Aftermany re-installs still no go....

Is there a package for this yet?
Can someone point me in 1 direction on how do do this.
Like i said I tried all the attempts that people have given and they all dont work.



PLEASE help....

p.s i have a Nforce2 chipset board...

---

### Post by floyd27 on 2005-09-07
These r the latest steps i have used.
I have kernel headers/gcc installed 
I tried with and without GUI (step "3")..



1. Download official driver .rpm from the ATI website.
2. Remove fglrx packages using synaptic.
3. Shut down gnome. [ From terminal: sudo /etc/init.d/gdm stop ]
4. cd to where you downloaded the driver rpm file.
5. sudo alien fglrx-4-3-0-8.16.20-1.i386.rpm
6. sudo mv /lib/modules/YOURKERNELVERSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. dpkg --force-overwrite -i fglrx-4-3-0-8.16.20-2_i386.deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. modprobe fglrx
13. fglrxconfig


However this does nothing.
I still get

roderick@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Also when i tried to do step "6" it said there is no such file or dir???? I may have moved it in the past, is that ok?
also do i have to remove the restricted repositories.(i have not )

any help would be great..

---

