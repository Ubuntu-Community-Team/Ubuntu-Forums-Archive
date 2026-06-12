---
title: "Only 3.5gb ram on 64bit?"
date: 2011-11-05
forum: Hardware
---

### Post by stewacide on 2011-11-05
Got a new, cheap, but should-be-fully-64bit-capable Acer laptop, w/ an Arrandale CPU and Ironlake graphics, and 4gb ram. Installed 64bit Ubuntu (came with Windows 7 but didn't note whether it saw all the ram), but Ubuntu only reports 3.5gb of ram once installed. If I boot into the firmware it says there's 4gb installed, with 128mb reserved for graphics.

I can't imagine Ubuntu is reserving 512mb for graphics? There's no option in the firmware to 'remap memory' or enable 64bit support or anything like that; given the age of the laptop (brand new; it's a 7739z) I can't imagine there's a 32bit limitation in the motherboard?

My best guess then is there's some 32bit-only driver holding things up. If this is the case does anyone know how to determine exactly what the culprit is?

This isn't a big deal from a performance POV, I'm mostly just curious :)

---

### Post by gordintoronto on 2011-11-05
Run Terminal, and enter these commands:
sudo lshw >myconfig.txt
gedit myconfig.txt

It might shed some light on the memory allocation.

My laptop, running 64-bit Ubuntu 11.10, has 3 GB of memory, and uses shared memory for the ATI video, 16 MB according to lshw. However, top says the total memory is 2,825,744K, or 2,893,561,856 bytes. About 300 million bytes seem to have disappeared.

---

### Post by stewacide on 2011-11-05
OK, think I figured it out. The integrated graphics are using 256mb, and for whatever reason the gnome settings panel aggressively rounds down the ~3.72gb to 3.5gb ram under system info.

---

### Post by robvas on 2011-11-05
What is the output of

[FONT=Courier New]uname -m[/FONT]

Are you sure you are running 64-bit? Also, what is the output of 

[FONT=Courier New]cat /proc/meminfo[/FONT]

---

### Post by gordintoronto on 2011-11-05
Interesting! Some memory has definitely "disappeared," on both my laptop and my desktop.

---

### Post by stewacide on 2011-11-05
> **robvas said:**
> What is the output of

[FONT=Courier New]uname -m[/FONT]

Are you sure you are running 64-bit? Also, what is the output of 

[FONT=Courier New]cat /proc/meminfo[/FONT]

Definitely using 64bit. Other apps report the correct 3.721gb of ram, it's simply the gnome system info panel that threw me off. Dunno' why it rounds so wildly.

---

