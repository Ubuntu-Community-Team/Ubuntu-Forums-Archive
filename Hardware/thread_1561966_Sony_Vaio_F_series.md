---
title: "Sony Vaio F series"
date: 2010-08-26
forum: Hardware
---

### Post by kingrobdun on 2010-08-26
I'm thinking of installing Ubuntu 10.04 on my New Sony Vaio F series   laptop. 
Specs: Quad core Intel core I7 processor (1.73Ghz) with Turbo Boost up  to (2.93Ghz)
Questions: Will I still be able to use blu-ray? 
What would run faster,  32bit or 64bit Ubuntu? 
Is there a way to disable the backlit keyboard?  
What are your personal  experiences with running Ubuntu on the F series?

---

### Post by heytbekankasin on 2010-09-01
I've been using my Ubuntu since the version 7.10 on my Acer 5920G laptop with Canonical upgrades. However my Acer laptop was broken because of unknown hardware malfunction. Therefore, I bought a new laptop which is Sony Vaio F12S1E/B (F Series) 2 days ago.

When I switch my Acer's SSD with Sony's HDD, Ubuntu easily recognize my new computer and greets with welcome screen.

However, sound cards are not recognized correctly. A quick search on google show me the sound card problem is fixed on new Alsa release. Ubuntu 10.04 is shipped with ALSA 1.0.21 and i need ALSA 1.0.23. So i follow the instruction on this site to fix my sound card problem

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

After all, my sound card is working partially correct. I said partially cause flash player can not forward the audio to my digital output and I've not found a solution yet. In addition to this, mic input is not working because of the kernel bug. This bug has a workaround, you can patch linux kernel 2.6.34, meanwhile Ubuntu comes with version 2.6.32, or you can compile and use 2.6.36 kernel which is including this patch already. I have not done this kernel upgrade because mic is not my priority right now, I prefer to wait the Canonical to release this kernel upgrade.

I don't have time to check the blu-ray movies are working but it can correctly read blu-ray disks. 

I'm using 64 bit version of Ubuntu because of the 8gb ram amount. It is pretty fast and stabil.

---

### Post by dahuda on 2010-09-05
I had the same problem.Thnx man. Worked fine. Appreciated !!

---

### Post by heytbekankasin on 2010-09-05
Ok so, new solutions for sony vaio f series notebook...

If you have Display Back light issue, follow this instruction for solution. It is easy to apply...

[http://code.google.com/p/vaio-f11-linux/wiki/DisplayBacklight](http://code.google.com/p/vaio-f11-linux/wiki/DisplayBacklight)

If you have display resolution problem and not to get 1600x900 or 1920x1080 resolution according to your sony vaio lcd display. Your xorg.conf file need some modifications for this.

Just add this following line to the device section on /etc/X11/xorg.conf file

    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"


The Device section should look like this

Section "Device"
        Identifier      "InternalCard"
        Driver          "nvidia"
        Option          "ConnectedMonitor" "DFP-0"
        Option          "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
        Option          "RegistryDwords" "EnableBrightnessControl=1"
EndSection

---

### Post by patatas on 2010-09-26
Just installed ubuntu 10.04 (64bit) on my vaio f series (i7, 6gb ram)

**Things that worked right away**
  - Networking/wifi ran right away after install
  - Display was working properly (but you need to install nvidia drivers if you want to use effects and other stuff)
  - LCD backlight can be adjusted through power management (but not yet using fn + f_)

**Things that dont work right away**
  - touchpad (but will work with an easy fix [http://georgia.ubuntuforums.org/showthread.php?p=9806445](http://georgia.ubuntuforums.org/showthread.php?p=9806445))
  - audio

**Wishlist**
  - it would be nice if the "light sensor" for the keyboard backlight worked, right now, the backlight would light up everytime you press a key regardless on the ambient lighting
  - lower processor fan speed, i dont know if fan speed is a bit high because temp is high, or it just really runs high

---

