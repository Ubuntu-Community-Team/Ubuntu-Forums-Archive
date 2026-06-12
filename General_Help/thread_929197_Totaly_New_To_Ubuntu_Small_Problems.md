---
title: "Totaly New To Ubuntu Small Problems"
date: 2008-09-24
forum: General Help
---

### Post by jonesyk on 2008-09-24
Hi all im moveing from ms to linux as ive been useing for ms for 8 years and want a change,Ive managed to get ubuntu onto my laptop but am haveing problems with graphics mainly my boot and log on screen not fitting also now and again getting funny lines down the screen.Its as if its a graphics driver issue i think its a via unichrome built in graphics gpu.

Any help on fixing my start screens would be grate i have searched on google and here but i tend to get lost quickly with been new.

Ive added 2 photo attachments to of the problem if it helps :)

---

### Post by TheGoodDocta on 2008-09-24
It looks like you may simply need to adjust your resolution within your xorg.conf...

Try running the following command at the command line:

sudo dpkg-reconfigure xserver-xorg

---

### Post by steveneddy on 2008-09-24
The issue is a setting in GRUB.

[http://ubuntuforums.org/showthread.php?t=258484&highlight=grub+resolution](http://ubuntuforums.org/showthread.php?t=258484&highlight=grub+resolution)

---

### Post by Bölvaður on 2008-09-24
If this is only on the boot up it is an easy fix.

There is a file that the boot loader (GRub) uses that holds the key to your answer.


it is the following file: /boot/grub/menu.lst

and you need vga=791 to be typed at the end of the command for booting up ubuntu.

use this command to open the file in gedit (with super user rights so you are allowed to change this system file). Btw commands are typed in the terminal found under Applications &#8594; Accessories &#8594; Terminal and you should drag that icon onto the panel where it is quick and easy to open (no mocking about in the menus)

```
gksudo gedit /boot/grub/menu.lst
```


Now you scroll down to the bottom of the file and look for something similar to mine

> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc8a4d6d-acb4-4012-955b-d2175046322c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

Insert "vga=791" behind the bootup commands like this

> kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cc8a4d6d-acb4-4012-955b-d2175046322c ro quiet splash vga=791


vga=791 means it is vga mode for 16 bit 1024×768  resolution.
you can also look up the table [here]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions") for a better suiting resolution.

---

### Post by jonesyk on 2008-09-24
tried both them methods and nothing happend added the vga to the line rebootd and it froze on every size.Just managed to edit the filr back and its let me log on any other ideas?

---

### Post by Bölvaður on 2008-09-25
yes, different bits could be what is wrong. so instead of 32 use 16 or instead of 16 use 8....

Any way, I cannot see this is a big problem if it is only the boot up. you can even disable the login screen so you will not be asked for login name and password, but it obviusly has security issue.. only use it if you are sure it is ok for you.

I would guess this problem will change (who is to say solved without definition of what is solved), in the next releash of ubuntu probably. this will probably also vary from distro to distro.

The first time I had ubuntu I had to change my vga=791 but the next releash fixed that problem, and the next one after that fixed every other problem I had except the all too fun ALSA vs OSS and the new Pulse audio. but I guess it will be fixed soon as puse audio seems to be gaining popularity so everyone will use it. which means no more audio problems.

---

### Post by pratikkaushik on 2008-09-25
Hello friends,
M also very new to linux.
I have installed ubuntu 8.04, on my laptop which is a intel dual core T2330 processor based laptop.
Ubuntu is installed and it runs fine but during shut down / logoff/ etc the display fades out and start showing black and white pixels and keeps changing colors.
Anyone please guide me to solve my problem

---

