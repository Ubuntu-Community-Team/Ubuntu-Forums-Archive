---
title: "Laptop keyboard, touchpad stop responding on startup"
date: 2011-02-04
forum: Hardware
---

### Post by honeysmiley on 2011-02-04
Hi 

I have recently installed Ubuntu on my laptop with Ubuntu 10.10.
Which i have installed with dual boot with windows 7
ultimate. I have Lenovo Y 500 series with Alps touchpad 
and Intel 945 motherboard, Celeron 1.6 Ghz processor with
2GB of ram.

It's problem is whenever i start up the ubuntu, touch pad and
keyboard stops working on User login screen. I have to use
my USB mouse and keyboard to move further and if i login
into Windows 7 it works absolutely fine.I have to restart
Ubuntu multiple times so that both can start working.
I have noticed one thing too. On User login window if
I put the system to Sleep mode  and bring backup
my keyboard starts working and but touch pad doesn't work. 

I don't know what kinna bug is this. I have tried multiple
things changing variables in Grub but it didn't work.
Updated the system completely, still no go.

Please help!! 

I really like using Ubuntu and i don't what's
going with it.

Any kind of help will be appreciated. :))

TC 
Harman

---

### Post by mukay on 2011-04-13
Hi,

i also have these problems on my acer tm2203lmi notebook. I'v found out that there is something wrong with the acpi. If u turn off acpi in grub by pressing 'e' on kernel in boot menu and add acpi=off at the end of line, than the keyboard works. I also read that this has to do with bug # 555169. But i cannot say that the problem is solved. I don't know what acpi has to do with keyboard and touchpad. Now i have an usb mouse connected so I can work. But I would find it better, if the touchpad would work and I won't be dependent of my usb mouse. Perhaps anyone can give more Information on how to get this problem solved.

lg

---

