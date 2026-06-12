---
title: "Another black screen. Desktop and nvidia"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by Jesper-L on 2009-02-04
Hey guys.
Ive been through a lot of black screen threads here and tried a lot of fixes out, but nothing helped me. So here it is for any ideas you might have.

Configuration:
P4 2,4 ghz
Asus P4PE mobo, 1 gig ram
Geforce 6600gt
Medion 20' flatpanel dvi/vga
80 gb sata hd

Everything is on clean install. Many clean installs :)

Problem:
After splash, the screen goes off for ½ a second and then turns back on, but only displays black. There are no drums or anything, ctrl alt f1 does nothing.

Initial installation goes fine, but activation of nvidia drivers makes the black screen after boot appear. I have tried all 3 drivers available after installation with same results. A driver directly from nvidia has also been tried but never made to run.

I have tried:
[LIST=1]
[*]envyng
[*]Different drivers as mentioned above
[*]Uninstalling compiz
[*]Both 8.10 and 8.04
[/LIST]

The problem persists in the exact same manner regardless of these things. I dont think any of those directions contain the solution. Since most of the black screens here are from ATI cards i have not pursued everything in those threads (i.e. the ati specific installation guide)

One little peculiar thing: DVI didnt report screenresolution so everything was done in 800*600 with that. Switching to VGA immediatly brought up my hopes since the original 1650*1080 resolution was immediately deteced. But the black screen still came tumbling.

I CAN boot to desktop if i boot in recovery mode and choose "Try to fix xserver". Ubuntu then reports that xorg.conf might have had invalid settings and hat they have been corrected. But it then goes on to boot without nvidia drivers.

Im about to give up, any hint of help will be very much appreciated.

---

### Post by inobe on 2009-02-04
now i have noticed that board supports agp 4x's max if i am not mistaken !

this may be the problem considering you have an 8x's video card.......

maybe in the bios disable fast writes or mess with various other agp settings

i looked up that board at asus, it did in fact say agp 4x's max

---

### Post by avtolle on 2009-02-04
Once at the desktop in safe-graphics mode, have you then tried to install the nVidia driver? Or, is this the step that you try to install the driver, with the resultant black-screen?

---

### Post by Jesper-L on 2009-02-04
Hey guys, many many thanks for the quick replies.

Im now looking into bios settings, its very well spotted i must say. I remember when i built the box i was affriad it could be an issue. Sofar setting the agp speed to 1x does not solve anything, i will continue to tamper with any agp related bios settings.

avtolle, installing the nvidia drivers after a succesfull recovery mode boot does not fix the problem either, no.

Thanks again

---

### Post by inobe on 2009-02-04
i think xserver needs reconfigured if the bios offers no help

something got tainted from the initial install and foobard xorg.conf

edit: remembering some things

if your running a card that uses additional power plug, that plug should not be connected to the video card on a 4x's slot, this will damage the card and motherboard

"verification needed that it's a 4x's agp slot"

---

### Post by Jesper-L on 2009-02-04
Hey again :popcorn:

I should add that this box has been running XP for quite some years, at first as gaming machine, later as the girlfriends desktop. Although i do see that the agp issue can come into play when changing OS, its not the gut feeling i have about it. I do have another graphics card though and i will test that before i give up, but its quite inferior to this GF6600 which is a nice card i think.

There was an advice somwhere about reconfiguring xserver from tty, which i have also tried, but did not help.

I have attached xorg.conf and zorg.conf. The first file is what boots the desktop and is what the recovery mode Try to fix xserver makes. zorg.conf is the nvidia adapted one that wont boot.

EDIT: attachment system required one more try :)

---

### Post by Jesper-L on 2009-02-04
The BIOS has options for 4x and 1x agp speed. The only thing i dont like about this being the reason is that the box has worked well for so many years.

There IS a normal 12v plugged into the card, it does not boot without it.

Do you think i should switch the card?

---

### Post by inobe on 2009-02-04
my suggestions are based on some experiences i have had


been threw the lost grub

been dropped to busybox

witnessed the infamous initramfs

the black screen with flashing cursor

sr0 error

i have corrected each listed problem, it was all related to hardware and configuration :D

granted' windows may have operated that setup' but we can't compare as this is no comparison, we are speaking of something that handles hardware differently.

when i said reconfiguration' this involves removing previous drivers "purging", reconfiguring xorg, getting a GUI, installing an nvidia driver.

i said that because' the initial install could have had trouble with a dvi connection, the further modifications contributed to the current results

possibly leaving in vga plug rather than dvi "if you already haven't tried" would have .........

---

### Post by inobe on 2009-02-04
> **Jesper-L said:**
> The BIOS has options for 4x and 1x agp speed. The 

There IS a normal 12v plugged into the card, it does not boot without it.

Do you think i should switch the card?

try a different card, it may help


i am uncertain of the hardware at the moment, that needs to be just so

---

### Post by Jesper-L on 2009-02-04
Hehe, inobe. I get the point, ill try changing it. 

When i mentioned the thing about VGA/DVI, i should have also mentioned that i reinstalled 8.10 after making the switch.

Whenever i fell i have messed things up beyond my abilities, i have made a reinstall. I think i maybe up to 10 now :). I really did try to solve it before posting in the forums, lol.

---

### Post by inobe on 2009-02-04
i cant find anything that says this card works in a 4x's slot

i don't know jesper

---

### Post by Jesper-L on 2009-02-04
I have now installed another graphics card, TNT2 64 MB memory. For the first time the resolution of my monitor is reported correctly. 

Only drawback sofar is that it runs like crap, hehe. I can sometimes see the screen redrawing from top to bottom. Ubuntu does not report the need to install nvidia drivers.

---

### Post by inobe on 2009-02-04
is the driver enabled in restricted drivers, what do you see in there ?

usually when you get that affect' it needs  a driver :)

---

### Post by Jesper-L on 2009-02-04
Hm, i think that maybe now i need to reinstall. Hardware driver program reports No properitary drivers are in use. But i think there should be - even an old card like that must need real drivers.

---

### Post by Jesper-L on 2009-02-04
Ill try envyng now.

---

### Post by inobe on 2009-02-04
don't reinstall ubuntu, wait for someone to reply, they may know exactly what to do:)


i have no experience with tnt cards "yet" in ubuntu

i have a tnt card i wish to put on a netserver that will be operated by ubuntu server addition, i will be sure to inform you when it's setup.

i may possibly refer to this thread myself' if anyone replies of course;)

---

### Post by Jesper-L on 2009-02-04
Well, on that one i dont think you'll really need it :). Ive done a few ubuntu server installs and when youre done with the install you might as well unplug that card again and do it all via ssh and webmin. Thats just an awesome combination that makes almost anything possible even for a noob like me. I have 2 of those servers running now.

Hm, envyng just messed things up even more, hehe.

---

### Post by inobe on 2009-02-04
yeah, i didn't think about it, text base haha

okay' i will go desktop and let you know

---

### Post by Jesper-L on 2009-02-04
Maybe i can offer you a bit of help then: TNT2 drivers does not support xserver 1.5 which is the one (i think) used in 8.10. So you should examine this first or just go for 8.04.

Which i will do now.

Many many thanks for the help, to any others finding this in the future: Check your hardware ;)

---

