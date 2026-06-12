---
title: "ubuntu is running in low graphics mode"
date: 2008-12-18
forum: Hardware
---

### Post by llwhitefangll on 2008-12-18
Hey i am a new linux user. and i just installed linux and it was working fine until i restarted the computer then a message came up and said "ubuntu is running in low graphics mode" "your screen, graphics card, and input device settings could not be detected correctly. you need to configure these yourself.

i don't remember the graphics card completely but i do remember that it was a ati radeon 128mb.

Also, before i restarted the computer i went to screen resolution and it said Hewlett Packard 22', but after i restarted it, it says unknown.

can someone please help me? :(

---

### Post by llwhitefangll on 2008-12-18
bump

---

### Post by nkri on 2008-12-18
If you are able to get to your desktop, go to Applications>Accessories>Terminal and copy&paste the following command
```
sudo dpkg-reconfigure xserver-xorg
```
When it asks for the sudo password, just type your regular password...nothing will show up, just type it and press enter.

Follow the on-screen instructions and restart.  Now you should be good to go!

If, however, you cannot get to a desktop, turn on the computer and press ESC when it says something about GRUB 1.5.  Now use the arrow keys to get to "...(Recovery Mode)" and hit enter.  It'll boot into recovery mode, then give you a short list of options.  One of them is something along the lines of "Repair X."  Go to this one and hit enter, then reboot into normal mode and you should be fine:)

Good luck!
-nkri

---

