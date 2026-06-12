---
title: "DELL live cd NIGHTMARE PLZ HELPPPP"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by l0fls on 2008-12-10
my dad gave me his old dell optiplex GX260 with windows first thing i did was try to install linux 8.10 from live cd
i set my bios to boot from cd i get error every time
"strike F1 to retry boot, F2 for setup utility"
if i strike F1 i get the same thing
if i go to setup utility i see that it is set up exactly the way i want it, to boot from cd.


please help peoples im desperate here
btw i searched forums but couldn't find any prior threads with resolutions that helped me.
:confused:

---

### Post by Rocket2DMn on 2008-12-10
Did you burn the CD correctly?  [uhelp]community/BurningIsoHowto[/uhelp]
You may also need to check the md5sum of the .iso image that you downloaded before burning it to a cd (links are on that page for how to md5sum and the Ubuntu hashes that you check the sum against).

There is also usually an option to enter the boot menu rather than changing the BIOS boot order - can you select to boot from the CD from there?

---

### Post by inobe on 2008-12-10
get imgburn to burn the cd, it detects bad discs better, it will check the disc after the burn for defects.

[http://fileforum.betanews.com/detail/ImgBurn/1128426215/1](http://fileforum.betanews.com/detail/ImgBurn/1128426215/1)


exclusively it will burn iso images.

---

### Post by l0fls on 2008-12-10
i burned ubunutu 8.10 2 times tried both disks, no luck
so i also tried other distrobution live cds i had lieing around
(backtrack 3, knoppix, plack, and ubuntu 8.04 all gave me no luck)

yes i set it to boot from CD first and disabled all other boot methods

as for the md5sum do you think that could be the problem even if i tried Several disks, and distorbutions.

---

### Post by Rocket2DMn on 2008-12-10
If you can't boot from any CDs that are burned correctly, I would say you have a BIOS or hardware failure.  I would reset the BIOS to defaults, and if that fails, try a different CD/DVD drive.  May also want to update the BIOS if possible.  CD drive are often the first pieces of hardware to die.

---

### Post by frankleeee on 2008-12-10
As the others posts suggest it may be a hardware problem, but when I look up the stock ram amount for this computer it is 128MB awfully low are you trying to install with the desktop CD or the Alternate. I believe the ram may be to low even for the Alternate with a Ubuntu distro.

---

### Post by abn91c on 2008-12-10
with you dell pc when you reboot press f12 then select boot from cdrom, that is all you have to do, no need to go into the bios

---

### Post by abn91c on 2008-12-10
with you dell pc when you reboot press f12 then select boot from cdrom, that is all you have to do, no need to go into the bios.But If you messed with the BIOS already reset it to factory defaults, then reboot and hit f12

---

### Post by l0fls on 2008-12-11
> **frankleeee said:**
> As the others posts suggest it may be a hardware problem, but when I look up the stock ram amount for this computer it is 128MB awfully low are you trying to install with the desktop CD or the Alternate. I believe the ram may be to low even for the Alternate with a Ubuntu distro.

:(
what should i do!?!?!?

---

### Post by l0fls on 2008-12-11
> **inobe said:**
> get imgburn to burn the cd, it detects bad discs better, it will check the disc after the burn for defects.

[http://fileforum.betanews.com/detail/ImgBurn/1128426215/1](http://fileforum.betanews.com/detail/ImgBurn/1128426215/1)


exclusively it will burn iso images.

thats dumb.... why would i burn isos with a .exe in wine?!?!?!?
i mean psh honestly who uses windows anymore.... jeez
:)
:lolflag:

---

### Post by frankleeee on 2008-12-11
I am not quite sure of the exact answer, have you have tried the other suggestions? Finding out the amount of ram would be a good start then if the computer is not having hardware problems ask about the better distro for what you actually have.

---

### Post by inobe on 2008-12-13
> **l0fls said:**
> thats dumb.... why would i burn isos with a .exe in wine?!?!?!?
i mean psh honestly who uses windows anymore.... jeez
:)
:lolflag:

my bad, i assumed the worst :lolflag:

---

### Post by l0fls on 2008-12-17
im just going to scrapp that old dell and my old sony viao (hadrive failing i belive) i have to FSCK every time i turn it on. and buy a laptop from cyber power pc, or rather my parents will buy it for me :D

---

