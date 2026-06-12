---
title: "ubuntu 9.10 on Qosmio x500 10q"
date: 2009-12-29
forum: Hardware
---

### Post by patfrat on 2009-12-29
Hello,
I have installed Ubuntu 9.10 on a Toshiba Qosmio x500 1Oq
Some problems :

- wifi does not work natively, i have had to compile the r8192se_pci driver
see [http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254)
Does Ubuntu 10.04 and the 2.6.32 kernel will resole it ?

- bluetooth is not activated until you do it through windows with the Toshiba software

- the microphone does not work

- the boot freeze 2/3 times until you delete the splash option in the kernel line boot in /etc/default/grub file and do a sudo update-grub

- the screen is shaking, is noisy, i don't know how to say it, when you log in a console with CTRL+ALT+Fn or close the session
perhaps the 185 nvidia driver is not completely the good driver for the nvidia gts 250 card ???

- the fingerprint is not working, recognized as an Attentec 2550

But this laptop is not mine and i can't now sending bug to launchpad !!
If you have the same laptop and same issues, you can help me and my friend having rhis laptop !
Thanks in advance !

Patfrat

---

### Post by RedSingularity on 2009-12-29
As for your video card......i have the same one.  Try using the Nvidia 190 graphics drivers.  Works great here!

---

### Post by patfrat on 2009-12-30
Ok, thank you ... so, you have no problem with this driver for the gts 250 !
I will try it.

---

### Post by patfrat on 2009-12-30
Ha, the driver 190 does not resolved the graphical issue ...
It is more a Usplash issue i think !
Another person has tested it ...
I have had also to remove the splash command at boot to boot alaways correctly !!! Is is Usplash too ?

---

### Post by RedSingularity on 2009-12-30
Do you have the driver selected in your xorg file?

Post the output of 

cat /etc/X11/xorg.conf

---

### Post by patfrat on 2009-12-30
I can't post the xorg.conf because this is not my laptop
but i will contact the owner to send me it.
But, after installing the 185 nvidia driver, the 3D acceleration is OK
It does not seem to be a nvidia issue for another qosmio x500 10q owner but perhaps because of usplash and the refresh rate !!!!

---

### Post by MoGa on 2010-01-07
I have x500 and I can confirm that the monitor problem still exist in Ubuntu 9.04 and 9.10 with the latest driver 190 and the beta 195 as well. Before I installed the driver, I had no problems with accessing the Alth+F2 console .. after trying all drivers its still obvious that the problem is from the Nvidia driver.

---

### Post by patfrat on 2010-01-08
Thank you for your reply ...
Is this laptop too young for us ? 
When laptop builders will work for all OS and not just Windows ?

---

### Post by MikeZ83 on 2010-01-16
Just stumbled over this thread because I encountered the same distortion problem on my X500-10U.

Karmic has all its latest updates and the driver can't get much more current than the 195 beta (problem occurred with the 185 and 190 as well). 
I first encountered the problem after only the vanilla install, the latest updates and the 185 driver were installed. 
On a sidenote, I also can't get beyond the "lock screen" dialog when trying to put the system into "suspend" or "hibernate" modes but I'm not sure that's caused by the same problem.

---

### Post by Fingyfin on 2010-09-23
Just thought I should say that I have Lucid (10.04) running on the same laptop. All is well except for the headphone jack not putting out sound at the moment. I have the AMD 64bit release running on it. 34bit did not even finish the install. Even got compiz fusion pimping it out (after the drivers were setup). Wireless works. Trying to tackle the headphone problem now.

---

### Post by cryptmod on 2011-01-11
I have exactly the same issue on my QOSMIO X500-149 , X, microphone, wifi,occational keyboard key not registering , except mine is [I]Maverick, and my xorg.conf:  Any suggestion would be appreciated.
 
[/I]> 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko/Epson"
    HorizSync       30.0 - 75.0
    VertRefresh     80.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 460M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

