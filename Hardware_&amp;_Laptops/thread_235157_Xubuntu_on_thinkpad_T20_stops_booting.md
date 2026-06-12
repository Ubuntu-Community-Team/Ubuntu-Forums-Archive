---
title: "Xubuntu on thinkpad T20 stops booting"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by zepski on 2006-08-12
I just relized that xubuntu had released a cd on Aug 7th.  I was using the cd released before that.  Downloading the older cd to see if it works.  Will keep posted.


-------------------------------------
System specs:
IBM Thinkpad T20
700Mhz P-3 moblie
128megs ram
20gig hard drive (not orginal)

I been using Xubuntu on my laptop for a few days.  It was runing fine and all until last night.  Last night I installed gnome because i wanted to see how well it would run on the system since its an older laptop.  The install went fine and I i then logedout reloged in with gnome for the new session.  It worked.  I shut down the computer for the night.

However the today when i turned it on it now freezes durning boot.

at first i would freeze and show: saving VESA state [OK]

So i figured i pop in the xubuntu cd to see if i could rescue it and it froze in same spot.

I next tried a regular ubuntu cd and it booted so i removed the partitions for the hard drive and rebooted with the xubuntu cd.

On this reboot it gets further:
it loads till it reads: Loading GNOME enviroment [ok] (think thats it) and then it freezes.

just for fun i rebooted it a few more times and each time it froze where was always a little differnt but it was always between VESA and the gnome part.

I was wondering what could be causeing this?  I would install ubuntu but the system i have needs a usb flash drive with a swap partiton on it just to install xubuntu.  So installing ubuntu is kinda out of the question (well speed wise)  unless i could install that then install the xumbuntu-desktop package no problem

---

### Post by zepski on 2006-08-12
Solved problem with booting all needed to do was add the acpi=off and it boted right up.

---

### Post by pierlo on 2006-10-28
thanks dude!this helped me a lot!

---

### Post by qriopal on 2006-10-28
I am trying to install Xubuntu Edgy Eft on the same model laptop (Thinkpad T20 with 128mb RAM) but it hangs up after I get the following message during booting with the liveCD:

"[   126.547156] piix4_smbus 0000:00:07.3: IBM Laptop detected, may corrupt your serial eeprom    Refusing to load module

* Activating swap...
mount: Function not implemented

* Checking file system...
fsck 1.39 (29-May-2006)

_"

Any Idea what the problem maybe? I tried to boot using this CD several times on this machine and every time the computer hangs up right after the above message during booting. I also tried acpi=off as a boot code. Doesnt work on my computer. The liveCD is working fine when used on my desktop with 512mb RAM. 

Hope someone can let me know what the problem might be.

---

