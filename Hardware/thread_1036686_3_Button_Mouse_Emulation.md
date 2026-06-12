---
title: "3 Button Mouse Emulation"
date: 2009-01-11
forum: Hardware
---

### Post by noab on 2009-01-11
Hello Folks!

I have a -hopefully- pretty simple question. Is there anyway to change the action performed when I press both mouse buttons at the same time. It usually emulates mousebutton 3 pressed, but I want it to emulate let's say mouse button 7 pressed.

Thanks!

P.S. Using 8.10 with all updates right now + Gnome

---

### Post by noab on 2009-01-11
Anything?

---

### Post by whymichael on 2009-05-27
Apparently the configuration of input devices is now accomplished through "xinput". This might help you.

[URL="https://wiki.ubuntu.com/X/Config/Input#Example:%20Disabling%20middle-mouse%20button%20paste%20on%20a%20scrollwheel%20mouse"]Example: Disabling middle-mouse button paste on a scrollwheel mouse
[/URL]

> I can view the current button mapping thusly:

$ xinput get-button-map "Logitech USB-PS/2 Optical Mouse"

1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 10

Really, only the first three numbers have meaning for me. They represent the left, middle, and right mouse buttons.

I can turn the middle mouse button off by setting it to 0:

$ xinput get-button-map "Logitech USB-PS/2 Optical Mouse" 1 0 3

Or I can turn the middle-mouse button into a left-mouse button by setting it to 1:

$ xinput get-button-map "Logitech USB-PS/2 Optical Mouse" 1 1 3

---

### Post by mark_a_kessler on 2011-02-24
Has anyone found an easy solution for this?

---

### Post by Popaul on 2011-05-02
I've got the same issue for Blender now that I switched to 11.04 Before Blender was able to emulate the middle button when I clicked left and right together, but now... does not work anymore. 
So I gave up and installed [http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)
You can find it in the Ubuntu Software Center. 
Easy :)

---

### Post by llamahunter on 2011-06-10
Same problem.  I verified that Emulate3Buttons is set to yes in my xorg.conf, so not sure what's the problem.

---

### Post by lightstream on 2011-09-18
+1 for GPointingDeviceSettings (listed in Software Center as Pointing Devices)

It doesn't let you set different functions for left+right click though: it's button 3 or nothing. The only other thing it lets you do is wheel emulation.

My mouse's middle button died, so this means I avoid having to buy a new mouse. 

You can also enable these by creating an xorg.conf file, but for some reason that stopped my keyboard working. In a way this is better as you don't need to log out for it to take effect.

---

### Post by etognoni on 2013-03-03
enrico@hp:~$ sudo cat /usr/share/X11/xorg.conf.d/10-evdev.conf

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Option "Emulate3Buttons"     "True"
        Option "Emulate3Timeout"     "100"
        Driver "evdev"
EndSection

i added Option "Emulate3Buttons" "True" and the following Option in file and now 3buttons emulation works.

---

