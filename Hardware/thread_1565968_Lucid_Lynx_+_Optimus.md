---
title: "Lucid Lynx + Optimus ?"
date: 2010-09-01
forum: Hardware
---

### Post by const451 on 2010-09-01
I am thinking of buying Sager NP5125 laptop that has Optimus technology. Does anyone have experience on how Ubuntu handles Optimus?

I know it is a very new technology; the Sager has Intel 4500 integrated and GeForce 330M descrete video cards.

THX!!

---

### Post by shteren on 2010-09-17
very very badly...

i have the np 5125 aswell, didn't think it whould be so hard getting nvidia drivers to work...

i hope 10.10 will fix this and get some update nvidia drivers.

meanwhile i tried using [this guide]("http://ubuntuforums.org/showthread.php?t=1056531&highlight=nvidia+177+unable+start") and [this one]("http://ubuntuforums.org/showthread.php?t=1495936") then i got a black screen...

no errors but something didn't work, so i looked a bit around and saw [this]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup")

tried to add it with the sager adress location in /proc/acpi/video/GFX0/LCD0/EDID.

and still black screen...

this is where i gave up, mybe someone with more experiance can help?

either way, getting the 256 driver into 10.10 whould be superb

---

### Post by const451 on 2010-09-17
Agh, it's a bummer with NP5125, definitely no go for me. 

Here is the link that helped me to install NVIDIA Drivers on Sony VPCF11 series laptop with NVIDIA 330M:
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

I modified the steps as you have to start/stop gdm:


*******************************************
Install NVIDIA proprietary driver:
*******************************************

1) Download newest Nvidia drivers

2) Open module blacklist as admin

    gksudo gedit /etc/modprobe.d/blacklist.conf

Add these lines and save:

    blacklist vga16fb
    blacklist nouveau
    blacklist rivafb
    blacklist nvidiafb
    blacklist rivatv

3) Stop GDM
   
   sudo service gdm stop

4) Uninstall any previously installed Nvidia drivers:

    sudo apt-get --purge remove nvidia-*

5) Reboot your computer

6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)

7) Login and cd to the directory where you saved your file, Install drivers

    sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run

9)Start GDM

    sudo service gdm start

10) might not be necessary:

After searching a bit I found on the page linked in the bottom of this post that Sony Vaio F's LCD panel EDID isn't recognized by nvidia drivers automatically, so you have to "help" drivers in this matter: after finishing installing nvidia drivers (and before the reboot) you have to add the following lines to "Device" section of xorg.conf:

Option         "ConnectedMonitor" "DFP-0"
Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"

---

### Post by shteren on 2010-09-17
i saw this guide, even posted a link to it in my comment.

well anywayz it's all because of this nouveau which is supposed to be open source nvidia driver. but it's anoyying, i hope next version fix it.

---

### Post by shteren on 2010-09-18
update:

i tried [this]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html") guide aswell, ended up in black screen...

tried to add the Cpnnected monitor trick and it didn't work...

mybe in sager it's not related to as DFP-0 or i'm using the wrong EDID?

but it seems like it's the same problem as on the vaio, the screen turns totally black, though everything is loaded correctly

---

### Post by const451 on 2010-09-18
I do not have this lappy yet, I'll have to find something Ubuntu frendlier...

Thanks a lot for your post!!!!

---

### Post by shteren on 2010-09-19
Ohh don't get confused! It is totally ubuntu friendly! Unless you plan on wine gaming with it.
You can easly force it to use the igpu to save power.
Every thing work great, even the dialup modem(?!).
Core stepping works great and can upclock only one core at a time.
Compiz also runs great.

---

### Post by const451 on 2010-09-26
sorry for double post

---

### Post by const451 on 2010-09-26
it's Linux friendly except the screen is all black :)

You're saying that I can disable Optimus with that button and run Ubuntu on integrated gfx with no problem?

I am not playing any games, just grad school work: c++, matlab, etc.

Thanks!

---

### Post by shteren on 2010-09-29
not with the bottow, there is a simle work around, i posted in another thread, can't link now sry, look for it.

---

