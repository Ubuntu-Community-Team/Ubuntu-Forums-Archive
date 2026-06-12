---
title: "Help!"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by MofoDmo on 2009-08-04
Does anyone know how to install ubuntu on an Acer Revo via a usb drive at all?

I'm not the best at computers so could someone provide a basic step by step guide haha :)

---

### Post by huggies15 on 2009-08-04
what OS do you have on it at the moment?
If you have windows xp then download a program called unetbootin. Get a new usb drive and use unetbootin to install ubuntu and make is act like a live boot cd.
Put the usb stick in your pc, restart, and choose to boot from the usb drive. the ubuntu live desktop should load with an option to install to the hdd. Follow the simple on screen instructions and your done.
Hope that helps, the program is pretty straight forward!
Steve

---

### Post by MofoDmo on 2009-08-04
> **huggies15 said:**
> what OS do you have on it at the moment?
If you have windows xp then download a program called unetbootin. Get a new usb drive and use unetbootin to install ubuntu and make is act like a live boot cd.
Put the usb stick in your pc, restart, and choose to boot from the usb drive. the ubuntu live desktop should load with an option to install to the hdd. Follow the simple on screen instructions and your done.
Hope that helps, the program is pretty straight forward!
Steve

I'm on some sort of splashtop thing that came with the Acer.
I think it's Linux i'm not sure! :(

---

### Post by huggies15 on 2009-08-04
do u have another pc u can use?
Unetbootin is on linux, but i dont know how to download anything in the acer OS.
On a side note, how do they look? ive been toying with the idea of getting one

---

### Post by MofoDmo on 2009-08-04
It's a pretty awesome computer if you can get a proper OS on it!
The Splashtop one is pretty horrendous and basic haha,

I'll give your idea a go on my laptop though and give you a little feedback on how i get on :)

*UPDATE* Just tried the Unetbootin idea and it still is on the Splashtop OS


Any more ideas?

---

### Post by jrox717 on 2009-08-04
when you start your computer, there should be a message along the lines of "Press f2 to get into setup"-- this could be esc or f1 or something else, it depends on the computer. In setup, you should be able to change the boot order--make sure the USB option is before the harddrive. This ensures that the computer will boot from the Ubuntu USB before Splashtop

---

### Post by MofoDmo on 2009-08-04
> **jrox717 said:**
> when you start your computer, there should be a message along the lines of "Press f2 to get into setup"-- this could be esc or f1 or something else, it depends on the computer. In setup, you should be able to change the boot order--make sure the USB option is before the harddrive. This ensures that the computer will boot from the Ubuntu USB before Splashtop

Yeah i've tried that, but still goes through to the splashtop OS.

---

### Post by ugm6hr on 2009-08-04
That should be easy...

I would recommend using the Ubuntu 9.04 Netbook Remix, since it is designed to be installed from USB, and comes with clear instructions on how to install from USB.  Just download the correct file from the Ubuntu home page.

I assume you can actually get to the boot order page, and the reason the Splashtop default loads is because your USB is not bootable (at present).

To convert from NBR to standard Gnome is easy.

Ask again when you get that far (or Google).

---

### Post by MofoDmo on 2009-08-07
*bump*

---

### Post by ugm6hr on 2009-08-07
> **MofoDmo said:**
> Yeah i've tried that, but still goes through to the splashtop OS.

If you have correctly changes the boot order in BIOS, and it still fails to boot into USB, there are 2 possibilies:

1. The USB is not bootable.
2. The BIOS is faulty.

Likely to be option 1; hence the suggestion to use NBR; I have found creating bootable USBs a bit hit-and-miss from iso files.

---

