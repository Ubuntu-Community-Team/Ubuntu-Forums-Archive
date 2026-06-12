---
title: "A Good Challenge to Install A Linux Distro - no CD, no USB, no ESC key, bad graphics"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by jephrei on 2009-04-06
i got this sweet (now i'm thinkin otherwise) Acer Travelmate C100 tablet notebook from a friend with xp on it. It's slow as hell so i figured Ubuntu or Xubuntu would be nice. 

Unfortunately, I can't install from a live CD cause there isn't any, I can't change the boot sequence to boot from usb before the hd because my "esc" key is busted so i can't save and exit the bios, which means a USB flash or USB cdrom boot won't work. My next step is using either grub, unetbootin, or wubi and install straight from the HD and i've tried them all. DamnSmallLinux (which is not what i want but i tried after the following distros failed) gets an error and brings me to the limited shell...fine...i don't want it anyway...would rather have Xubuntu or Ubuntu. But when i tried installing them the loading progress bar loads (it actually loads on Xubuntu by filling the bar from left to right but just bounces back and forth on Ubuntu) and then it flashes 3 times with a sort of interlaced garbled loading screen then goes blank. i also can't get into safe graphics mode because my esc key doesn't work and i can't get into the menu at bootup. i'm assuming it either has to do with RAM (256) or my video card or something. i'm pretty sure i tried Ctrl+Alt+F1 and Ctrl+Alt+F2 because i've read it switches the video settings but that didn't work.

this has been a damn fine challenge for me but i need serious help from you guys and gals. i've seen EVERY web page on the issue and it's driving me crazy. i'd like to format everything once installed and to be honest, usng the tablet would be nice but it's not necessary at this point. i'm sure i can install drivers later if i want. so that's it. thanks for reading all that and ANY ideas would be great.

---

### Post by 0cton on 2009-04-06
Fix the keyboard (Seriously)
or buy a usb keyboard
The problem lies in the keyboard so fix it (its like you came here asking how can i install ubuntu when my screen is broken so i dont know were to click,) just your keyboard's esc key is broken and you cant change bios boot order, you can't install any os that way it has nothing to do with ubuntu but with your keyboard needing fixing (its ridicoulous )
Seriously... (Fix the God-damn keyboard!)

---

### Post by upchucky on 2009-04-06
it is choking on the vid card, but u can fix everything by fixing the esc key, new keyboard for that notebook is about $20.00


or since it has a usb floppy you can press I think the temp boot select key is F12 and boot from it,
or you can create a usb bootable flash drive and F12 boot it then install from the flash, 
or you can also use a usb external drive and F12 boot it then install from there,
or you can boot from floppy and network install if you have a network.

---

### Post by ronparent on 2009-04-06
Check it out jephrei, 1)the usb is often the default boot drive in more recent laptops (ie if the usb is in place on boot it will be examined first). 2) I exit and save bios setting from all my four computers with the F10 key (admittedly it varies from board to board).

---

### Post by 0cton on 2009-04-06
also you can jump through pages and on the last page (ussualy) should be a save save and exit discard discard and exit or something similar and you only need enter for that (unless you enter BIOS by esc with i understood to not be the case) nonetheless fix your keyboard

---

### Post by jephrei on 2009-04-06
@upchucky really? $20? i'm pretty sure i have to send it in to change the laptop keyboard, no? i was HOPING i could do this all for free.

@ronparent the esc key (which is busted as you know) is the only thing that gets me out of the bios and saves...F10 doesn't do anything. a USB flash doesn't work cause i have to set it in the BIOS. would a USB keyboard work even if USB is not bootable? would the USB keyboard even work in BIOS?

@octon. i understand what you're sayin but you could've been cooler about it. being a computer geek yet a linux newb i figured you and the rest of the community would maybe know somehting about the screen flashes which are independent to ubuntu and xubuntu or lead me to a key remapper (which i realize can't be done for BIOS). but i do appreciate your help. you guys came with some quick resposes. by far the most alive forum i've been on.

---

### Post by SR_ELPIRATA on 2009-04-06
I havent seen your tablet PC but Ive had some troubles with a Dell that has a huge keyboard problem. I didnt wanted to invest money on it since also the battery needs replacement, but just by plugging a ps2 keyboard.... I can use it. So I'd suggest the same, either PS2 (if u have the port) or the USB option should work for the BIOS at least.

ELP

---

### Post by upchucky on 2009-04-06
usually there is a plastic strip that u remove first then maybe 2 small screws to lift the keyboard, one small ribbon connector to disconnect, reverse procedure to install. be gentle with the ribbon connector do not bend it, it has a pressure fit type clamp.

google the machine for instructions, dell has complete service assembly instructions for all their laptops free on their site.

ebay the keyboard, or tiger direct.

---

### Post by jephrei on 2009-04-06
really? a USB will work in bios without the USB ahead of boot sequence? cool...alright...i'll try that i guess. anyone know of why the flashes are happening? cause if i fix that, the bios and esc key and whatnot aren't an issue.

---

### Post by upchucky on 2009-04-06
screen flashes are the graphics trying to start, this can be fixed after the other problems are fixed.

see stuff about manual settings for resolution and display type

---

