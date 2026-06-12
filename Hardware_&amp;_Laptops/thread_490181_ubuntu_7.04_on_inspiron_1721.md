---
title: "ubuntu 7.04 on inspiron 1721 ?"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by alex1974 on 2007-07-02
Hello,

has somebody experience with ubuntu feisty on an inspiron 1721 notebook?#
I think about byuing one (now 879 Euro) but want to stick to ubuntu. OTOH without support it's a waste.
Please, need help,
Alex

---

### Post by linuxwizard on 2007-07-02
Look around in these links to find the model that you are looking to buy might be some info that will help you decide if you want to buy or not.

[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

[http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html)

---

### Post by alex1974 on 2007-07-03
I checked both links but nothing about inspiron 1720 or 1721. I googled too but nothing. So maybe someone has more experience then me and can help.

-----------------------------------------------------------------------------------
The details:
Intel® Core™ 2 Duo Prozessor T7100 (1,80 GHz, 800 MHz, 2 MB L2-Cache)
2048 MB 667 MHz Dual-Channel DDR2 SDRAM [2 x 1024]
17,0" Breitbild WXGA+ (1440 x 900) TFT-Display
SATA-Festplatte mit 160 GB (5.400 U/Min.)
Internes 8x DVD+/-RW-Laufwerk mit Software
nVidia® GeForce™ Go 8600M GT mit 256 MB dediziertem DDR2-Grafikspeicher
899 €
--------------------------------------------------------------------------------------

Thanks in advance
Alex

---

### Post by alex1974 on 2007-07-06
OK, finally I decided on an Inspiron 1520.
Has anyone experience with it?

---

### Post by JC_510 on 2007-07-12
Bumped.

Purely because I am looking at getting this laptop, and am interested on any information that anyone has!!

---

### Post by linux23dragon on 2007-07-14
[QUOTE=JC_510;3009298]Bumped.

I'm happy to say that I was able to install Ubuntu-7.04 on a Dell Inspiron 1520.  But.... there is a trick to installing it.

You need to install Ubuntu-6.10 first.  Then upgrade to Ubuntu-7.04 (using the update manager).
You will get all the bug fixes that's currently available for Ubuntu-7.04 during the upgrade.


The Ubuntu-7.04 installation disk has driver (and possibly HAL) issues with the Dell Inspiron 1520 SATA controllers.
The default linux-2.6.20.X kernel  possibly fails to load  the correct SATA drivers if you first try to boot from the Ubuntu-7.04 installation disk.  So you end up finding youself looking at the ash shell (loaded by busybox).


The upgrade solution to Ubuntu-7.04 works, because the kernel (as with other software) has already been updated to 2.6.20.15.


At the moment I'm having issues with the DVD burner.  But that will be solved as soon as I start looking to make it to work.


This is a list of what works (out of the box) so far, by upgrading from Ubuntu-6.10 to Ubuntu-7.04:-

internal Wifi card (Intel) 
Ethernet
Bluetooth
Nvidia 8600M (change the the video driver "nv" to "vesa" (found in /etc/X11/xorg.conf) when you first use/install Ubuntu-6.10)
HD Sound card (you need to recompile the "Alsa drivers",  "Alsa libs" and "Alsa-tools"  for better sound quality.  You may also need "Alsa firmware").
USB ports
Display
Keyboard
mousepad (with mouse buttons)


Not yet working correctly out of the box:-

DVD  +/- burner (works O.K. With Ubuntu-6.10)
Web cam.  (You might need to install the UVC Driver ([http://linux-uvc.berlios.de/drivers](http://linux-uvc.berlios.de/drivers))  for it to work)


Have not tested:-

Internal modem
PS2 connectors
VGA output
Audio input/outputs
Firewire IEEE1492


The DVD burner might start working correctly in the next kernel/HAL/DBus upgrade.

I'd say that most (if not all) issues will be solved once Ubuntu-7.XX will come out in October.

Hope this helps

I've started a new thread ([http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)) with this very post so people can easly search for this information.

---

### Post by moniquita66 on 2008-01-14
I tried installing Ubuntu on a Dell 1721, but the partition is not recognized.
Has anyone been able to solve this problem? or is the 1721 not recommended to run Ubuntu?

Thank you!

---

### Post by dcmalllory on 2008-01-26
I have the Inspiron 1721, and am running 7.04 on it with no problems.

I did the manual partition setup and installed the software from the Alternate CD - it won't run on the other as the xorg server won't start. Once the software was installed, I ran "Envy -t" on it, and did the manual install for the ATI driver. I have the resolution of 1920x1200.

For the wireless card, I downloaded the drivers from the dell site, and then used ndiswrapper to set the card up.

Everything else worked right out of the box.

7.10, however, is a different beast. Ndiswrapper never worked to load the wireless, there is no sound, and the whole unit just acted strange. I went back to 7.04, and once again am happy.

Hope this helps.

DCM

---

