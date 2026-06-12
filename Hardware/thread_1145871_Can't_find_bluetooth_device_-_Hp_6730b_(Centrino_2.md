---
title: "Can't find bluetooth device - Hp 6730b (Centrino 2)"
date: 2009-05-02
forum: Hardware
---

### Post by jords on 2009-05-02
I'm having a strange problem with getting bluetooth to work on my hp 6730b- I can't seem to find a bluetooth device, but the bluetooth works fine in vista so it must be there :)...

lspci, lshw, and lsusb: [http://pastebin.com/f33252528](http://pastebin.com/f33252528)

I can't see a bluetooth device anywhere in there..

[http://www.linlap.com/wiki/HP-Compaq+6730B](http://www.linlap.com/wiki/HP-Compaq+6730B) and [http://en.gentoo-wiki.com/wiki/HP_6730B](http://en.gentoo-wiki.com/wiki/HP_6730B) say that the laptop's bluetooth is supported in linux, and gentoo-wiki says: BT: HP branded Broadcom, supported by bcm203x module

The bcm203x module is loaded according to lsmod.

hcitool dev lists no devices and the gnome-bluetooth app can't find any either... 

Anyone know what could be going on here? Never had a issue with hardware i know exists not showing in lspci or lsusb before...

Thanks
Jordan

PS: Running ubuntu, but installed ubuntu-desktop from my kubuntu install so i have both installed. I have a few of the kde bluetooth apps installed but they don't work either

---

### Post by jords on 2009-05-03
bump?

---

### Post by jords on 2009-05-13
Just in case anyone else has this problem:

I've found the solution to this: I dual boot with vista, and in the hp wireless manager software on vista i had disabled bluetooth to save power ( and just enabled it when i need it) - It seems that if it's disabled in the vista software, the device doesn't even appear to the computer. - And this holds over reboots. So when i enabled it in the vista software and rebooted bluetooth worked immediately.

---

### Post by firfin on 2009-05-19
Wow. Amazing.. you can really seriously f**k up your computer when using vista. Time for serious driver support under linux. If this bluetooth chip was well supported under linux this wouldn't be happening.

---

### Post by jords on 2009-05-19
I don't think it's so much the support of the actual broadcom chip, but I think the hp windows software is sending a special signal to a hp chip on the motherboard to turn it off.

So Linux just needs to be able to interface with this chip, but i imagine it's quite specific to each laptop model....

---

### Post by blaize1310 on 2009-06-04
I have the same problem with my 6730b but I only have Ubuntu so does anyone have any ideas on how I can turn it back on:confused:

Thanks

Tony

---

### Post by blaize1310 on 2009-06-10
bump :p

Surely I don't have to install windows to fix this problem????

Tony

---

### Post by blaize1310 on 2009-06-22
Ok I have fixed this and YES you need windows natively install, i.e. not virtualbox or vmware to install the HP Wireless assistant. Once you turn bluetooth on in windows it just works in Ubuntu :D

Tony

---

### Post by djeek on 2009-10-27
A simple "Restore defaults" in the BIOS will fix this. :D

---

