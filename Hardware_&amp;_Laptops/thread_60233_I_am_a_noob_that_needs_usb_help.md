---
title: "I am a noob that needs usb help"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by thebilko on 2005-08-26
Ok I am definitely a noob to linux. I have only used it for a day or two. I am running a Compaq Armada 7400 and I am trying to get my usb drives to work. Now on this desktop that i put ubuntu on (someone built it) it automatically detects my drive but when i plug it into this laptop it lights up but i can't figure out hos to access the files. now i did go to the root terminal and type dmesg|tail and i got this.

sda: Write Protect is off
sda: Mode Sense: 02 00 00 00
sda: assuming drive cache: write through
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in

like I said. I am a noob and i need to get this drive working please help. feel free to email me at [email]sam_mcdavid@comcast.net[/email]. I am pretty experienced with windows computers but now i feel very retarded and i need some major help. 

also i typed in ps aux or somthing like that in the root terminal and i didn't see anything about disfuctioning or somthing like that. thanks in advance for any help.

---

### Post by thebilko on 2005-08-27
[QUOTE=thebilko]Ok I am definitely a noob to linux. I have only used it for a day or two. I am running a Compaq Armada 7400 and I am trying to get my usb drives to work. Now on this desktop that i put ubuntu on (someone built it) it automatically detects my drive but when i plug it into this laptop it lights up but i can't figure out hos to access the files. now i did go to the root terminal and type dmesg|tail and i got this.

sda: Write Protect is off
sda: Mode Sense: 02 00 00 00
sda: assuming drive cache: write through
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in

like I said. I am a noob and i need to get this drive working please help. feel free to email me at [email]sam_mcdavid@comcast.net[/email]. I am pretty experienced with windows computers but now i feel very retarded and i need some major help. 

also i typed in ps aux or somthing like that in the root terminal and i didn't see anything about disfuctioning or somthing like that. thanks in advance for any help.[/QUOTE]
 also i checked the device manager and it shows up in this device manager

---

### Post by atrus325 on 2005-08-27
Noob here too, and I really only know anything about Gentoo, so I probably won't be too much help.

Anyway, you've probably already tried this, but:

mkdir /home/(yourusername)/Desktop/usbstick
mount /dev/sda /home/(yourusername)/Desktop/usbstick

J.

Edit: it might also show up at sda1 or sda2

---

### Post by thebilko on 2005-08-27
i looked in my dev folder (and i have it set to show all files) and i could not find anything about sda and i kept getting kind of error about it in my terminal but the closest thing that i have to it is hda

---

