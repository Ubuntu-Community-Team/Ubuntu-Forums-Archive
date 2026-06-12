---
title: "Graphical Error"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by FRigax on 2008-02-19
When I upgraded to the then latest version of Feisty Fawn several months ago, I encountered an error where the resolution would constantly be set to 640 x 480 even though my screen supports up to 1650 x 1080. After some tinkering, I thought I solved the error but when I logged back on, I encountered another strange graphical error. I don't really know how to describe it other than my screen seemed to have had parts of it turned diagonally. Attached are pictures or my login screen, my desktop, and a detail shot of my desktop (sorry about the terrible quality). I've got an ATI Mobility Radeon HD 2300 and haven't updated ubuntu in months because I haven't been able to see what I've been doing. Any help would be greatly appreciated.

---

### Post by Yellow Pasque on 2008-02-19
Boot into recovery mode and use the link in my signature to install the radeonHD driver.

---

### Post by FRigax on 2008-02-19
I tried following those instructions but after putting in the first command, *sudo apt-get install build-essential git-core configure-debian automake autoconf xorg-dev libtool*, I got an error message saying "Could not resolve 'us.archive.ubuntu.com'

It suggested that I try *apt-get update* and appending *--fix-missing* to the end of the command. I tried both but got the same error again. Any suggestions?

---

### Post by Yellow Pasque on 2008-02-19
I'm guessing your internet doesn't work in recovery mode. Can you get to a terminal by booting in the regular manner and pressing Ctrl+Alt+F1?

---

### Post by FRigax on 2008-02-19
That worked. I got through the first three command lines but after executing the third one, the instructions say, "In the Section "Device" area that is showing vesa, avivo, or fglrx, change the Driver '<driver-name>' line to radeonhd." I didn't know where to find this and I can't see anything outside of the terminal. I tried just proceeding to the next command but got an error saying "cannot open display." Is there a way to update the xorg.conf to reference the new driver in the terminal? Oh, and thanks a bunch for your help so far.

---

### Post by Yellow Pasque on 2008-02-19
Yes, you can use vim to edit text files.
```
sudo vim /etc/X11/xorg.conf
```
When vim first starts, it's in command mode. Press the 'i' key to turn it into a normal text editor. When you're done, press 'Esc' to go back to command mode and type :x[Enter] (that's a colon followed by an 'x') to save the file.

---

### Post by FRigax on 2008-02-19
Alright. I'm in a freshly updated Gutsy and everything appears to be running smoothly. However, the visual effects are unbelievably slow, even with no effects enabled. Even scrolling up or down in windows is almost unusably slow. I believe that my graphics card should be able to handle this, as it plays Team Fortress 2 perfectly well at medium settings. Anything I can do about this?

---

### Post by Yellow Pasque on 2008-02-19
The radeonhd driver doesn't support 3D acceleration or compiz at the moment. The latest word from the developers on the ETA was "several months, at least" :\

---

### Post by FRigax on 2008-02-19
I don't suppose there's another driver I could try, is there? Anyways, thanks so much for your help.

---

### Post by Yellow Pasque on 2008-02-19
You could give ATI's drivers another go
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

