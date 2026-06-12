---
title: "Gateway lt22 keyboard and mousepad BIG problems"
date: 2010-09-08
forum: Hardware
---

### Post by arturobar on 2010-09-08
Hello! for the past 4 days i've searching for a solution on this problem, as soon as I enter the ubuntu GUI the mouse and keyboard of my netbook stop working and the GUI is pretty lagg, after a lot of research i tried adding this 'i8042.nomux=1 locale=fr_FR i8042.reset' to the /etc/default/grub file and update it, but it didn't work, then i thought it could be grub so i downgraded to grub legacy, still no luck, after that i thought the distro was causing problems, it was 10.04 so i downloaded 9.10 and tried everything above with no luck... aldo i tried netbook remix and i can't get it to work i need it cause geany is THE IDE to code, hope someone can help me with this 

P.D. wired keyboards and mice seems to work perfect, laggy but perfects 
cheers skill

---

### Post by Ouel on 2010-09-13
i have the exact same problem !
ive read somewhere on this forum that acer has release a bios update for their AcerOne (with exact same  processor/ati)...

let me know if you fix this problem !

10.10 failed...
fedora 13 failed...

---

### Post by freefaling on 2010-09-22
same problem with me. i made a bootable usb of ubuntu 10.04. it booted fine, went well until the desktop screen. cursor just won't move!

tried the 10.10 beta first, hoping it would have better hardware support. that one didn't even boot fully.

Netbook: Gateway LT2207H

---

### Post by t.giguere on 2010-10-15
Same problem here: Touchpad and keyboard don't work as soon as Ubuntu is booted, on Hard Drive or on USB stick using Live.

Noticed EXTREME LAG (as laggy as tryin to run flash while the Visual Studio C++ debugger is running (that's 98% of the RAM right there ;) )

Also, a lot of mouse and effects lag when the fglrx ati/amd drivers aren't active. When you do activate them, there are a lot of artifacts, windows where everywithing is slanted sideways, etc.

Some Fn combinations do work though, the ones related to the display: brightness, external output, backlight on/off. volume and wireless aren't triggered though.

---

### Post by Ouel on 2010-10-15
you may try the last post of this thread...
tell my if it works for you

[http://ubuntuforums.org/showthread.php?t=1549086&goto=newpost](http://ubuntuforums.org/showthread.php?t=1549086&goto=newpost)

---

### Post by t.giguere on 2010-10-15
I'm kinda afraid lol. He says not to try it if we don't have the exact same specs and from what I see the acer has Bluetooth while the LT2207h doesnt...

---

