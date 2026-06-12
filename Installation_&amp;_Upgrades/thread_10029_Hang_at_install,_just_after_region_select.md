---
title: "Hang at install, just after region select"
date: 2005-01-04
forum: Installation &amp; Upgrades
---

### Post by tAK on 2005-01-04
Hey guys, 

i just recieved my Ubuntu CDs in the mail, took the live CD for a spin (very nice... couldnt be happier)

then decided to go ahed with a hdd install, but no luck...

my system:
AMD Athlon XP 2600+ (Barton)
512Mb RAM
ABIT NF-7m (with nVidia GeForce 4 integrated graphics)
Seagate 160Gb ATA 133
NEC ND-1300A DVD burner..

The EXACT issue:
I boot off of the cd, press enter to install, and then select "english" as my language, it goes to the next section, and i select "Australia" as my country.

the next screen that comes up is all blue, except for a grey bar, and black indicator at the very bottom. i cant type here, and when i press enter it goes onto a new line, the grey moves up the screen and the word/letters typed stay there.

i have tried leaving it here (for upto and hour) with no luck, it just stops.

anyone here offer any help?

thanks
/tAK

---

### Post by tAK on 2005-01-04
[QUOTE=tAK]Hey guys, 

i just recieved my Ubuntu CDs in the mail, took the live CD for a spin (very nice... couldnt be happier)

then decided to go ahed with a hdd install, but no luck...

my system:
AMD Athlon XP 2600+ (Barton)
512Mb RAM
ABIT NF-7m (with nVidia GeForce 4 integrated graphics)
Seagate 160Gb ATA 133
NEC ND-1300A DVD burner..

The EXACT issue:
I boot off of the cd, press enter to install, and then select "english" as my language, it goes to the next section, and i select "Australia" as my country.

the next screen that comes up is all blue, except for a grey bar, and black indicator at the very bottom. i cant type here, and when i press enter it goes onto a new line, the grey moves up the screen and the word/letters typed stay there.

i have tried leaving it here (for upto and hour) with no luck, it just stops.

anyone here offer any help?

thanks
/tAK[/QUOTE]
 *UPDATE*

just went at got anoter CD of it, and the same thing happens.... i have tried 3 different install disks, with no luck

please help
/tAK

---

### Post by jbh on 2005-01-04
weird. pick another country? :D

---

### Post by tAK on 2005-01-04
[QUOTE=jbh]weird. pick another country? :D[/QUOTE]
 tried that... no luck, i would pick another language just to test... but dont want to risk obliterating my XP partition...

how do i start a custom install? as at the moment i am going the default... maybe a custom install will skip the problem...

unfortunately, ALL of the CDs i have are doing this, and i dont have another computer to test them on... so it will be a while until i know if it is the CDs or my hardware.....

it will be a bummer if it is the CDs as they were for distribution at my Local LAN...

/tAK

---

### Post by F Cocquyt on 2005-01-05
[QUOTE=tAK]

The EXACT issue:
I boot off of the cd, press enter to install, and then select "english" as my language, it goes to the next section, and i select "Australia" as my country.
[/QUOTE]

Same thing here except the installation already hangs at the language selection (I want to select Dutch). I can't even select a language or only for a brief period. I move up a few lines and it hangs. 
I've downloaded the iso version last night from the site, burnt it and am now trying to get it installed. Tried it already several times. Every time the same thing  ](*,) .

My PC:
Dell inpiron 8000 laptop. 
( 800 MHz Intel Pentium III, 512 Mb Ram)
Currently dual boot with WinXP and Fedora Core 3.

---

### Post by tAK on 2005-01-05
[QUOTE=F Cocquyt]Same thing here except the installation already hangs at the language selection (I want to select Dutch). I can't even select a language or only for a brief period. I move up a few lines and it hangs. 
I've downloaded the iso version last night from the site, burnt it and am now trying to get it installed. Tried it already several times. Every time the same thing  ](*,) .

My PC:
Dell inpiron 8000 laptop. 
( 800 MHz Intel Pentium III, 512 Mb Ram)
Currently dual boot with WinXP and Fedora Core 3.[/QUOTE]
 this is most interesting, i am using version 4.1 aswell. but my CDs are all factory pressed. and i haev tried 20 different ones...

now could someone please tell me the command to type at boot to do a CUSTOM install?

PLEASE..... i think it is custom, but i aint sure

/tAK

---

### Post by tAK on 2005-01-06
[QUOTE=tAK]this is most interesting, i am using version 4.1 aswell. but my CDs are all factory pressed. and i haev tried 20 different ones...

now could someone please tell me the command to type at boot to do a CUSTOM install?

PLEASE..... i think it is custom, but i aint sure

/tAK[/QUOTE]
 *UPDATE*

i got ubuntu installed.... the fix: Try another CD-rom drive... in my case, i used a Samsung CD burner, to install from (with thanks to a mate leaving his computer unatended...) either way, it is done, installed just fine

the next problem (and it seems to be a common one)
Xfree86 fails to load on boot... it tells me to try and restart gdm after it has been properly installed, i ma using the default graphics card, built into my mother board...

ABIT NF7-m, any one else useing this board? and having issues....?

personally, i dont see why the Ubuntu installer is so bug ridden, its on its ver4 release... i hate to think what its pre-realease or BETAs were like... *shudders*

anyways, the Live CD boots just fine.... and its GUI runs extremely well... why can the Live CD boot, and auto config everything, but the HDD install cant? anyways.... enough commenting

i have run the Xfree86 config as described in another post:

reboot into recovery
root$ (a command which does NOTHING, so i assumed it meant o run the command as root, and sudo to it, which is what i did)

xf86config

this started the config... i went through it, and answered everything right... and it saved the config file.... but still no GUI... even after a reboot and running:

sudo -s
/etc/init.d/gdm start

please help, i REALLY want to give ubuntu ago... but this is a LOT more work then i expected to have to put it.... 

/tAK

---

