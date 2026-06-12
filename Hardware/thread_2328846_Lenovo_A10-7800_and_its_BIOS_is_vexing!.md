---
title: "Lenovo A10-7800 and its BIOS is vexing!"
date: 2016-06-24
forum: Hardware
---

### Post by tuskpc on 2016-06-24
I hate writing for help but after a month with this problem I'm at my wits end!

First the PC details:
Lenovo A10-7800  Radeon R7  12 Compute Cores  4C+8G
Product:  90BG003JUS
Serial:  R3022LS8
BIOS:  IRKT56AUS

Problem:  Every "how-to install" on the internet does not match my computer [example: there is NO UEFI option to click once you reboot, nor there a Boot option in my BIOS (how is that possible!) thus everything is USB and I have no option to change that to DVD]

Note: I somehow installed and partition Ubuntu (1.3TB) with my horrible Windows 10 (480GB) with a DVD and yet I CANNOT get GRUB to work and thus it keeps going straight to this horrible Windows 10.  Today, after I reboot, even the "boot-repair-disk" I burned to a 1GB USB froze up while loading.  What do I have to do to get this to work?!  I have used Windows this month more than I have for almost 6+ years (you could probably combined those years!).  This is ridicules!

---

### Post by banceu_sergiu_ione on 2016-06-25
In order for your pc to run, it must have a bios ( or as its newly replacement uefi ... call it however cuz they do the same job, start run the pc ).

Now, I'm not sure what OS you try to install but ubuntu 16.04 need more then 1GB USB stick. On mine, it size at 2GB.

Here is how to create a [bootable USB from windows]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") which you need it. Maake sure the USB stick you use have all the requirements ( at least 2GB size ).

Get this good, so will you not have issues after install. Make sure its all created as have to be, may save you time after install to see what had went wrong.

Make sure you deactivate the ' fast startup ' from windows 10. This is important in order to make your c really shut off.
Now you really have to find out how to enter your bios( uefi ).

There might be a Lenovo Center System installed  on windows. Check it and see if you get anything that show like a UEFI with order boot/ special key / memory and stuff like that. If it is, then use it to change the boot order, deactivate special key FN, set your pc on max performance too, take off any suspend option you set in windows.

If you do not find it, then try this:

fast startup set on off from windows ---- this is important to do it

shut down the pc -  turn it on and press ' ENTER '  .... did you got up UEFI ? then you navigate it and select the option you need

shut down the pc - turn it on and while you keep FN press F1 / check it with FN+F2 if not work at 1st. If your pc turn on fast you might as well be fast to get it work.

none work, then surface your windows and try deactivate as well the special key FN / fast start up off

try again ' Enter ' or F1 or F2 or ESC .. you might need to turn off each time 1 command not work.

Hope any of this options get you inside UEFI

---

