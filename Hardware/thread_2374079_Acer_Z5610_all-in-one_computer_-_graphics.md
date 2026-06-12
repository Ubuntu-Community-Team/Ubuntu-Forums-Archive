---
title: "Acer Z5610 all-in-one computer - graphics"
date: 2017-10-12
forum: Hardware
---

### Post by jonatangee on 2017-10-12
Hello,

I'm desperately trying to install Ubuntu 17.04 on an Acer Z5610 all-in-one computer. It features a 23" screen (full HD) and a GeForce GT240 graphic card.
First, I need to manually disable the ACPI upon booting (but then it works).
The biggest problem is that it uses some default xserver driver which provides me with a... 640x480 resolution.
nVidia driver version 340 is the good one for that graphic card. But I can install it via apt-get or manually from the nVidia website, in all cases after rebooting my screen puts itself on test mode.
I changed almost all settings possible in xorg.conf. I browsed all the forums.

I don't mind using nVidia or nouveau, but I obviously need to reach the 1920x1080 definition.
Btw I tried Linux Mint as a test, it provides a software-rendered 1024x768 resolution (already better but...), and when installing nvidia it's exactly the same.
It's like if my screen is not recognized.

Any hint?

Kind regards,

Jonatan Geeurickx

---

### Post by Autodave on 2017-10-12
The correct way (in my opinion) to install the Nvidia driver is to go to Settings -> Additional drivers and let it search and chose the best driver for you.

---

### Post by jonatangee on 2017-10-12
Hello,
I tried it but it leads to the same situation. After rebooting, I have a "test" screen (flashing white, black and color lines).

---

### Post by roberto3176 on 2017-10-20
Hi Jonatan,

I have the same love it/hate it computer. Ubuntu is installed and runs at 1920x1080. This mode is forced through GRUB:

sudo nano /etc/default/grub

and

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1080

---

### Post by jonatangee on 2017-10-20
Hello,

I tried it but it changes nothing here :(

Jonatan

---

### Post by roberto3176 on 2017-10-20
Desolé, didn't specify that I was running 16.04 on nouveau rather than nVidia...

My Xorg.conf is minimalistic:

Section "Device"
Identifier "n"
Driver "nouveau"
EndSection

Don't know why this works :confused:

Did you update-grub afterwards? Is grub in 1920x1080?
Never got nVidia beyond test mode though, seems that the EDID of the monitor is missing.

---

