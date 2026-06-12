---
title: "Middle button scroll on T61p Lenovo Laptop"
date: 2010-09-15
forum: Hardware
---

### Post by hankhaines@gmail.com on 2010-09-15
I just upgraded my laptop to the 10.10 Maverick desktop version of Ubuntu and my T61p Lenovo laptop middle scroll button has stopped working.  I have been working with Ubuntu for years and have been able to handle this pretty simply before by updating the xorg.conf file.  I ensured the that the file looks like: 

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ImpPS/2"
        Option "Emulate3Buttons" "true"
        Option "ZAxisMapping" "4 5"
EndSection

but without luck.  I have tried different options with more information about the mouse that I have for example:

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "Buttons" "5"
        Option "Device" "/dev/input/mice"
        Option "Name" "TPPS/2 IBM TrackPoint"
        Option "Protocol" "ExplorerPS/2"
        #add the following lines
        Option "Emulate3Buttons" "true"
        Option "Emulate3TimeOut" "50"
        Option "EmulateWheel" "true"
        Option "EmulateWheelTimeOut" "200"
        Option "EmulateWheelButton" "2"
        #end
        Option "Vendor" "Sysp"
        Option "ZAxisMapping" "4 5"
EndSection

even though from my experience the first version is all that I needed, and I have not been able to get it to work.  Any help will be greatly appreciated.

---

### Post by ajgreeny on 2010-09-15
Are you sure you need an xorg.conf at all for your mouse to work?  I was under the impression that most mouse buttons worked out of the box these days with no interference from an xorg.conf.

I may be wrong, but if so I am extremely lucky as my mouse, a Trust Ami Mouse Dual Scroll, with two scroll wheels and two side buttons works perfectly with me doing nothing extra, and certainly nothing in my xorg.conf about my mouse.  I get the standard forward/back in both Firefox and nautilus from the two side buttons, which in previous Ubuntu versions required **xbindkeys** running at session startup, and an .xbindkeysrc config file in my home.  This is no longer needed.

EDIT:

It appears I was wrong about the xbindkeys requirement.   It is definitely needed still, as evidenced by a rename of my .xbindkeysrc config file, following which the forward/back buttons no longer work in nautilus, though they still do in Firefox.  I think it is also needed in the **system->preferences->startup applications** listing.

Sorry for any confusion!  Perhaps you should look into xbindkeys for your problem?

---

### Post by DesertF0x on 2010-09-20
I have a similar problem with Maverick. 
Everything is working fine with trackstick configured over /etc/init/trackpoint.conf [(Link, sry german)]("http://wiki.ubuntuusers.de/Trackpoint#Einstellungen-permanent-machen-ab-Ubuntu-9-10") and gpointing-device-settings but after resume from standbye all settings are gone.
Any ideas?

---

### Post by blaer on 2010-10-11
So did i on my X61. It turns out that in gpointing-device-settings i had configured 4th mouse key as the button for "mouse wheel emulation". Which worked great in 10.04. Now, in 10.10, i had to change it to the 2nd key to get scrolling working again.

---

### Post by DesertF0x on 2010-10-11
Does the scrolling still work after resume from standbye?

---

