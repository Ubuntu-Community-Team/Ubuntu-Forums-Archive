---
title: "Ubuntu killed my laptop!"
date: 2011-08-16
forum: Hardware
---

### Post by Ollie13 on 2011-08-16
Ok. I have Acer Travelmate 2310 and i installed Ubuntu 11.04 to it. Before that there were no problems (except that i got bored with WinXP), but after that installation there were no backlight, so i couldn't see anything without flaslight or external monitor.

I thought that everything would have fixed back to way it was if i just reinstall Windows and drivers for my Acer, but wait - there is still no backlight! Is it possible that Ubuntu-installation did some serious damage to my laptop? I really dont know what to do.:confused:

And sorry my bad english!

---

### Post by MG&amp;TL on 2011-08-16
There should be no reason why software can damage hardware, at least in my book. Laptops do fail, and if that had XP on it, it's likely past its sell-by date.

I imagine the most likely thing is that the monitor failed on an inconvenient moment when you booted ubuntu for the first time.

That said, sudden hard-drive shake-ups can cause weirdness. But rarely. And not to do with the monitor.

---

### Post by coffeecat on 2011-08-16
> **Ollie13 said:**
> i just reinstall Windows and drivers for my Acer

Perhaps you didn't install all the drivers needed. Manufacturers produce special drivers for the backlight brightness and most manufacturers have several different implementations for brightness needing different drivers. Are you sure you installed the right one(s)?

Also, did you install XP from a Microsoft disc or from an Acer restore Disc? If from an Acer restore disc for your particular machine it should have included all the special drivers.

---

### Post by Ollie13 on 2011-08-17
> **coffeecat said:**
> Perhaps you didn't install all the drivers needed. Manufacturers produce special drivers for the backlight brightness and most manufacturers have several different implementations for brightness needing different drivers. Are you sure you installed the right one(s)?

Also, did you install XP from a Microsoft disc or from an Acer restore Disc? If from an Acer restore disc for your particular machine it should have included all the special drivers.
XP is from Microsoft disc, but i installed everything from that Acer's own supportpage ( [http://support.acer-euro.com/drivers/notebook/tm_2310.html](http://support.acer-euro.com/drivers/notebook/tm_2310.html) ). Quite frustrating :(

I got that used laptop for present this summer so i don't want to throw it away or anything like that, all i wanted was getting rid of Microsoft and start using Ubuntu. But it seems to be little harder than i thought it would be.. Sorry about all this non-ubuntu related wining, but after all that Ubundoing is my final goal with this :)

And thank you both for noticing!

---

### Post by coffeecat on 2011-08-17
> **Ollie13 said:**
> XP is from Microsoft disc, but i installed everything from that Acer's own supportpage ( [http://support.acer-euro.com/drivers/notebook/tm_2310.html](http://support.acer-euro.com/drivers/notebook/tm_2310.html) ). Quite frustrating :(

I don't see a driver in that list which seems to be specifically for your brightness control - unless either of eManager or GridVista do the job. I would guess that there's one driver for all the Fn key combinations, but what Acer call it I don't know. Possibly "wmi" may be in the driver name - The Linux driver for (some/most) Acer laptop Fn keys is acer_wmi because this function is implemented through ACPI-WMI. It might be worth looking on the Acer website for pages for related Acer models in case the driver was accidentally omitted from the page you linked.

Alternatively, you could contact Acer to see if they could provide a restore CD/DVD for that model, but that might be expensive.

**EDIT**: Found this page:

[http://support.acer-euro.com/drivers/downloads_gd.html](http://support.acer-euro.com/drivers/downloads_gd.html)

Select "notebook" and then your model and you will get to a page with some drivers listed but also a clickable link -"Need to know the hardware on your system..." Click on that and it will download an executable to search your system for hardware. Perhaps that might help.

---

### Post by Ollie13 on 2011-08-17
> **coffeecat said:**
> ...**EDIT**: Found this page:

[http://support.acer-euro.com/drivers/downloads_gd.html](http://support.acer-euro.com/drivers/downloads_gd.html)

Select "notebook" and then your model and you will get to a page with some drivers listed but also a clickable link -"Need to know the hardware on your system..." Click on that and it will download an executable to search your system for hardware. Perhaps that might help.
Tried that but it didn't find anything to fix. Next i tried to find some Acer 2310 recovery CD-torrents but didn't find any. And just a minute go i tried to register my laptop for Acer's support pages, but it said that my product's serialnumber is not valid (i think it is) and now i'm waiting for them to answer me or send me those damn drivers. 

Anyway, thank you for your help sir Coffeecat, i appreciate very much! :)

---

### Post by coffeecat on 2011-08-17
Good luck! :)

---

### Post by trundlenut on 2011-08-17
Have you tried using the function key to try and increase the brightness?

---

### Post by MG&amp;TL on 2011-08-17
My grandma did that, trundlenut. :D

---

### Post by trundlenut on 2011-08-17
I couldn't understand why the sound was working on my desktop when I installed Ubuntu, after about 15 minutes I realised I had turned the volume control on the speakers all the way down...

---

### Post by MG&amp;TL on 2011-08-17
Ah, simple hardware-based flaws. So simple to deal with...:)

---

