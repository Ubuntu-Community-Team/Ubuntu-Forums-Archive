---
title: "Live CD HP Pavilion n5470 boots sometimes"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by gegreen on 2006-07-05
(when I attempted to post this the first time, got an odd message about invalid forum.  so if this actually did post already, please disregard).

My HP Pavilion n5470 laptop (info below) behaves oddly when I attempt to boot the Dapper Live CD.  When I attempt to boot from powerup, it freezes between "Configuring X" and "Preparing restricted drivers".  When, however, I boot up Windows (Win2k Professional, SP 4) first then insert the Live CD then "restart" -- the Live CD boots up just fine.  (FWIW, Knoppix Live dvd 4.0.2 boots just fine every time)

This behavior is reproducible.

I'd love to installer Dapper on this machine but I'm reluctant to do so ... for obvious reasons 8)

Thanks for help.

Laptop info:
HP Pavilion N5470
    mobile Athlon 4 processor (1 GHZ)
    1 GB (crucial, a.k.a., micron) memory
    Toshiba MK2016GAP (20 GB) hard drive
    Trident Video Accelerator CyberBlade-XP 
    Toshiba DVD-ROM ( / CD-RW )
    Accton EN2242 Series MiniPCI Fast Ethernet Adapter
    ESS Allegro PCI Audio
    
    Phoenix Bios (rev GD.M1.08)

---

### Post by mrtrblmkr1 on 2006-07-17
I too have somewhat the same problem with
the Pavilion n5470. I haven't tried the DVD,
as I'm already sketchy with the LiveCD.

I haven't tried from Windows since I wanted a
straight ahead install from the LiveCD.
Using this line at boot:

live gdth=disable:y

I see that the problem lies in a Kernel Panic,
something with the fs not syncing, I'm not sure.
As a linux newbie, I'm just scrawling the net for
any help, I did work Xubuntu on my iMac but have
yet to install it. Knoppix runs nicely as a LiveCD
but it's just too difficult to install at the moment.

---

