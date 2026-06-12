---
title: "Solution to colored lines in logout"
date: 2009-04-27
forum: Hardware
---

### Post by trespuntos on 2009-04-27
Hi to all. Heres my little story
I have installed ubuntu intrepid 8.10 on my Hp dv2845 (dv2000 series). But when i logged out the screen got corrupted(check atachment). I tried EVERYTHING and i mean everything but nothing helped So i gave it up and worked 6 months with a corrupted screen. When ubuntu 9.04 came out last thursday i installed hoping the problem got solved BUT it wasnt. Everything worked fine but the screen in logout. So i decided to solve the problem and again i tried everything, heres a list

-Remove splash from grub: Doesnt worked
-Install restricted drivers: Doesnt Worked
-Remove restricted drivers install latest nvidia drivers from website (180.51): Doesnt worked 
-Changed gdm timeout form 10 to 60: Doesnt Worked
-I maded a copy of my Xorg and changed almost everything on it: Doesnt Worked so i restore my original Xorg from the copy i maded

I maded all this changes on an fresh 9.04 install and the problem seemed to continue, so i gave it up(again) and continue with my life and decided to install everything on the new ubuntu. I installed almost everything i use and the same. BUT when i installed (and im asumming that was the change factor) startup manager, webcam or pulseaudio AND I SUSPENDED my laptop i rebooted it and IT WORKED, NO MORE COLORED LINES ON LOGOUT.
So if youre having the same troubles i had give it a try, maybe we are getting closer to the solution. 

Guide i followed to install webcam and pulseaudio:
[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)

startupmanager was install from repositories.

AND HERES MY XORG CONFIG :
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

---

