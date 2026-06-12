---
title: "[SOLVED] x wont start"
date: 2008-09-17
forum: Hardware
---

### Post by water_foul on 2008-09-17
Starting with a fresh install, upon booting i got a black screen where keyboard input was useless so i want into recovery mode and ran "Xorg -configure" then, after testing it with "X -config /root/xorg.conf.new", I copied it into my xorg file (cp /root/xorg.conf.net /etc/X11/xorg.conf). Now when i run X I get a screen with a bunch of dots and an X which moves with my keyboard, when i run xinit I get a console with a garbled font which will load firefox, and when i run startx it errors after flashing giving the following output (- the headder)
```

expected keysum, got XF86KbdLightOnOff: line 70 of pc
expected keysum, got XF86KbdBrightnessDown: 71 of pc
expected keysum, got XF86KbdBrightnessUp:72 of pc
expected keysum, got XF86KbdLightOnOff: line 70 of pc
expected keysum, got XF86KbdBrightnessDown: 71 of pc
expected keysum, got XF86KbdBrightnessUp:72 of pc
Could not init font path element /usr/share/fonts/X11/cyrillic, removing fron list!

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing
```

I love ubuntu and would like to get it running on this computer (which happens to be a gateway tablet) so any help will be greatly appreciated.

Note: there could be typos because all functions and logs are and will be retyped onto another computer

---

### Post by water_foul on 2008-09-17
any one?

---

### Post by phidia on 2008-09-17
Are you using hardy? The command for resetting your xorg has been > sudo dpkg-reconfigure -phigh xserver-xorg  but under the new xorg with hardy sometimes you need to use other commands. See the revised xorg in hardy [here]("https://help.ubuntu.com/community/Video").

Added this:
The command > xfix has been recommended by at least one of the forum staff here. Unfortunately there is little or no documentation (no man page anyway) for that command.

---

### Post by water_foul on 2008-09-17
Yes I am using Hardy, last time i tried xfix I had no luck, Will try sudo dpkg-reconfigure -phigh xserver-xorg and post back

---

### Post by water_foul on 2008-09-17
No dice, using dpkg-reconfigure and xfix I get back to the black screen with no keyboard response, the only thing that still does anything is the caps lock key which changes the light

Edit: :O I just spilled the beans

---

### Post by water_foul on 2008-09-17
any other ideas?

---

### Post by water_foul on 2008-09-17
After research I found that my monitor is a Samsung ltn140w2-l02 if that helps

---

### Post by water_foul on 2008-09-18
I found in my Xorg.0.log that all of the default modes show (insufficient memory for mode) (bad mode clock/interlace/doublescan)(hsync out of range)

where the memory errors are in the more usual resolutions (like 800x600)

I am also using the vga driver

---

### Post by water_foul on 2008-09-18
Got my problem solved using the irc aparently the vga driver cannot start X, I had my video set to use the vga driver, as soon as I changed it to vesa it worked!

---

