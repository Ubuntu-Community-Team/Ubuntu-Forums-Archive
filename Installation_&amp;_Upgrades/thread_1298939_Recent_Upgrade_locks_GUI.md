---
title: "Recent Upgrade locks GUI"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by dodtsair on 2009-10-23
I updated my system last night and the result completely locks out the GUI.

All I see is the loading screen in bad colors shrunk at the top tiled across the screens with whole bundle of green and red lines through it.

Attempting to switch to a text tty has failed using alt ctl F1-6.  I was able to ssh into the box and turn off gdm permanently.  Now I can get to text prompts, but I use this as my only desktop machine.

Here is my xorg.conf file which worked before upgrade:


Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 3840 1200
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
EndSection

I have tried the failsafe, which worked before the upgrade with no luck:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

I have tried resetting the configuration with sudo dpkg-reconfigure -phigh xserver-xorg.  Even this config does not work.  I get: 

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Something outside the configuration of X has completely taken down my graphics.  I tried rolling back the kernel to earlier versions and none of those works.

There is mention that no input devices are detected but both the mouse and the keyboard work for the text login.

Attached are my logs

---

### Post by cybergalvez on 2009-10-23
have you tried reinstalling the radion drivers?

---

### Post by dodtsair on 2009-10-28
I have not, considering that the vesa driver did not work I did not consider it to be a graphics card driver problem.

However it does not hurt to try.  I reinstalled the radion drivers and no go same problem.

---

### Post by dodtsair on 2009-10-28
Is this the problem?
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.

---

### Post by dodtsair on 2009-10-28
I have added a bug for this issue:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/462716](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/462716)

Since I do not know that much I could not add much detail.  I will add more detail as it is revealed to me.

---

### Post by dodtsair on 2009-10-28
I think the following installations broke my server
Setting up linux-headers-generic (2.6.28.16.21) ...
Setting up linux-image-server (2.6.28.16.21) ...
Setting up linux-restricted-modules-server (2.6.28.16.21) ...
Setting up linux-server (2.6.28.16.21) ...
Setting up linux-libc-dev (2.6.28-16.55) ...
Setting up poppler-utils (0.10.5-1ubuntu2.4) ...

Can someone tell me how to revert back to the previous version.

---

### Post by dodtsair on 2009-10-28
If you look at my Xorg.0.log you'll see that my hardware configuration has two graphics card.  1) an ati 2) a nvidia.

I have been using the ati with the radeon drivers for months now and quite pleased with the quality.  However since for reasons as of yet unknown the ati radeon was not working for the radeon drivers or for vesa.

I decided to go into the bios and turn off the ati radeon card as it is an onboard video chip.

You can see from the attached logs, same behavior.  It loads thinks it is successful but this time all I get on my screen is black.  Nothing nada.  So this does not seem to be specific to the graphics driver.

---

### Post by dodtsair on 2009-10-29
So I think if I could roll back the kernel install I might be able to recover this system.  However I do not know how to tell apt-get to remove one version of the package and install the other version.  Especially since I do not know what version was removed.

---

