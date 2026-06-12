---
title: "non VGA problem on HP compaq"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by gliks on 2007-07-26
Hi, 

Im planning to get ubuntu 7.04 feisty on my HP Compaq Presario F551AU AMD64 X2, with graphics card NVIDIA GeForce Go 6100.

When I put in the live CD, the screen goes black radiant after the loading, so I chose to change the VGA at the start up of the live CD by pressing F4. 
Changing from VGA to 1024x786x32 .. and it works!
So I installed  ubuntu, but now I have the same problem with my ubuntu installation. 

How do I change this VGA to non-VGA in my installation like the live CD F4 button??
does this mean that I have to use VESA in my /etc/X11/xorg.conf ? if so how? As I couldn't find the word vga in that file. 

I tried to change the resolution screen from ubuntu live to change my ubuntu install, but that didnt work at all. 
I can only run my laptop using ubuntu live(non VGA) now, I dont even know how to get console from my install.

Please help. 
Thanks.

---

### Post by gliks on 2007-07-27
I have found the solution, sharing this for everyone on compaq F500

Got this from this website:
[http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500/](http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500/)
====
vga=792

to the end of the boot command. When you first boot the live CD, press F6 and add that command at the end of the line. This will let you boot into the graphical shell.

You will need to do this later to the grub bootloader menu in /boot/grub/menu.lst - simply add the directive to the end of the kernel boot command. That’s it, it all worked from there. Some minor issues with the NVIDIA drivers, desktop effects and Beryl, so I’m using none of those. I’m going to try the newly released NVIDIA drivers over the weekend.
=====

Also I fixed the wireless problem, that is suggested by the same website,
from here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Also for the record that runs dual core AMD straight away

Thanks.

---

