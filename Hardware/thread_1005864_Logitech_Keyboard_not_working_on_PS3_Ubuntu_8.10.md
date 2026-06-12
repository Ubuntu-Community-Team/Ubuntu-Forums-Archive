---
title: "Logitech Keyboard not working on PS3 Ubuntu 8.10"
date: 2008-12-08
forum: Hardware
---

### Post by akareh on 2008-12-08
I followed the instructions on another thread and using my usb keyboard and mouse was able to get ubuntu 8.1 on my ps3. It took me a while to figure out how to connect it to the wireless lan and I have to do it manually every time but oh well... The bluetooth keyboard shows up when I scan for bluetooth devices and I am able to get it to tell me that its working but it is not. I found some threads on other forums and I found taht I have the latest BLuez version but I can't seem to get it to work. Has anyone run into the same problem? any suggestions?

---

### Post by ielliott on 2008-12-29
I'm having the same issue with both my keyboard and mouse.

Its detecting it but then it doesn't work.

I'm pretty new to this, but I can't seem to find any documentation about Bluez.

When i do hcitool scan i find both my keyboard and mouse, using the GUI tool i can add the keyboard it will ask me to type in the PIN and i do and it says it is successfully paired, but i still can't type.

In the GUI tool, I see a KEY, and i can't find any documentation that says what that means

I also added an HCID.conf like was mentioned in some of the help things i found, but i don't believe that's a file that is read anymore.

I added this which is my keyboard and mouse to try and get it to work on start up.

device 00:07:61:B1:9F:71 {
name "Logitech diNovo Keyboard";
auth enable;
encrypt enable;
}

device 00:07:61:B3:2D:87 {
name "Logitech Mouse";
}

Any help would be appreciated as right now I would like to use my PS3 to stream video from my PC

EDIT:

I just installed bluez-compat and it installs hidd. I was able to do hidd --search and it foudn and connected booth my keyboard and mouse.

After reboot they still don't reconnect but working is better then not at all.

---

