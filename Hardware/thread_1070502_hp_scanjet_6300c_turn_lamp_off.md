---
title: "hp scanjet 6300c turn lamp off???"
date: 2009-02-15
forum: Hardware
---

### Post by stinger30au on 2009-02-15
i have aquired a hp scanjet 6300c scanner and im using it via usb

it works just fine and does everything i want it to do

with one small exception

the scan lamp runs all the time

even if i unplug the usb cable and turn the machine on, the lamp stays on all the time


from what i gathered from googleing round the net, this lamp can be turned off if your using windows and installed the hp software in the control panel

apparently in control panel in windows theres a setting , just a simple tickbox to turn lamp off

anyone know how i can do this in ubuntu??
at the moment i unplug it when not being used for extended periods of time as the lamp is used for scanning and i dont want to shorten them life of it by having it run 24x7

any ideas???

thanks

---

### Post by stinger30au on 2009-02-20
last night i unplugged the usb cable again and this morning the scanner when i came back in to the room where the scanner is it decided to turn the lamp off

looks like it needs to be unplugged from the usb cable for some hours before it shuts down, but i dont know exactly how long for

---

### Post by ihatetryingtopickaloginna on 2009-02-20
Mine only stays on four or five minutes. It has worked the same way under OS/2, Windows, and now Ubuntu. I never used the HP software that came with it, just used an image viewer's 'acquire' function. I had to with OS/2 since the HP software wouldn't run under it to begin with. I haven't even thought about trying it under wine.

---

### Post by geraldm on 2009-02-20
man scanimage

# to work,  the backend would need to support this command.  It may work without "1" after -n ?   This command probably does not work with every scanner.

scanimage -n1 {device}

---

### Post by stinger30au on 2009-05-03
in case anyone cares


this issue has been resolved in 9.04


the scanner goes to sleep on its own now

---

