---
title: "microsoft keyboard and mouse"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by ronoc on 2006-08-03
Hi folks,

I have been trying to configure my xorg.conf file inorder to use my wireless keyboard and mouse. keyboard and mouse make is microsoft and the model numbers are 1.0a and 2.0 respectively. 
My conf file looks like this

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

From the onset this did not look promising. When I plug in the usb hub one of the lights blinks faintly. Has anyone had any experience with this. 
Some help would be much appreciated.


Conor

---

### Post by cantormath on 2006-08-03
> **ronoc said:**
> Hi folks,

I have been trying to configure my xorg.conf file inorder to use my wireless keyboard and mouse. keyboard and mouse make is microsoft and the model numbers are 1.0a and 2.0 respectively. 
My conf file looks like this

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

From the onset this did not look promising. When I plug in the usb hub one of the lights blinks faintly. Has anyone had any experience with this. 
Some help would be much appreciated.


Conor

Is it a usb keyboard and mouse.
Like any other brand would probably work..........:roll:

---

### Post by ronoc on 2006-08-03
its a wireless keyboard and mouse.
I know what you mean. I have just tried editing the xorg.conf
with instructions from here ...
[http://katze-mit-wut.azundris.com/archives/126-Microsoft-IntelliMouse-Explorer-2.0,-linux,-xemacs,-and-x.org.html](http://katze-mit-wut.azundris.com/archives/126-Microsoft-IntelliMouse-Explorer-2.0,-linux,-xemacs,-and-x.org.html)

no show.
i reckon i might have to sell it off and buy another make.

---

### Post by cantormath on 2006-08-03
> **ronoc said:**
> its a wireless keyboard and mouse.
I know what you mean. I have just tried editing the xorg.conf
with instructions from here ...
[http://katze-mit-wut.azundris.com/archives/126-Microsoft-IntelliMouse-Explorer-2.0,-linux,-xemacs,-and-x.org.html](http://katze-mit-wut.azundris.com/archives/126-Microsoft-IntelliMouse-Explorer-2.0,-linux,-xemacs,-and-x.org.html)

no show.
i reckon i might have to sell it off and buy another make.

I would be suprised if that keyboard is supported at all, but dont loose hope, if it seems like it could be a common problem, the linux community finds a way.

I have a wireless mouse that works with my laptop, what kinda of wireless are the mouse and keyboard?

---

### Post by ronoc on 2006-08-04
hmmm I reckon I might have to go shopping for another keyboard and mouse...
thanx for the help.
C

---

### Post by Janlon on 2006-08-04
This one bugged me for a while - both my mouse and keyboard are Microsoft wireless jobs (same Model no's in fact), connecting through the same receiver. As with you, plugged it but all I got was a faintly flashing LED. The answer was simply to use the USB to PS/2 connector that shipped with it for the mouse - I'm sure you can get one from a good electronics store if you haven't got one - and the PS/2 connector on the receiver for the keyboard. Cheaper than buying a new keyboard and mouse!

---

### Post by ronoc on 2006-08-05
I would if only my laptop had ps2 inputs. My only option is to go usb.
Thanks for the suggestion though. 
I think I'm 
](*,) 
with this one.


C

---

