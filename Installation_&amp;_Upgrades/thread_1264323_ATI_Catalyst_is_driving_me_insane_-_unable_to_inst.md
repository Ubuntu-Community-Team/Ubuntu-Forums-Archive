---
title: "ATI Catalyst is driving me insane - unable to install driver"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by Zerp64 on 2009-09-12
My old Nvidia card busted (it was an old 6200... the components literally exploded. Just... don't ask....) So I got another card today. It's an ATI Radeon 4650 512MB by Diamond, and it has specs nearly doubling my old card. I installed it and the newly-purchased PSU and installed the driver on my Linux side - no troubles there. Took a few seconds.

But I cannot for the life of me install the drivers on my Windows XP side, which sucks because all of my games are on that side. I've uninstalled my old Nvidia drivers and used Driver Sweeper to make sure everything was gone, but I'm still recieving the "Setup did not find a driver compatible with your hardware or operating system. Setup will now exit" message. I honestly don't know what to do here... I can't play Freelancer or anything! 

O/S: Windows XP

Platform: HP Pavilion a800n

RAM: 1GB

PSU: 450w (with a shiny blue LED light...)

V/Card: ATI Radeon HD 4650 (512MB DDR2 AGP)

S/card: Soundblaster Live! 5.1 Surround

Mouse: Logite- Okay, I'll stop....

------------

I have the most up-to-date mobo drivers too. Everything's shiny and up-to-date, except for this darn card... I'm already off to a bad start with ATI...

Someone help me out?

---

### Post by Zerp64 on 2009-09-13
Okay, I've fixed my Windows problem. Turned out I needed a hotfix for AGP cards before I could install the drivers (they couldn't include the hotfix in the driver install .exe itself?). But now my problem has flipped. I will say this based on my current experience.

**ATI sucks for Linux.**

First thing I did when I booted into Ubuntu is download and install the ATI drivers from their site. The install process went fine and Compiz worked smoothly, so I thought I was done until I played a video... or even did _anything_ with my computer. I can do basic stuff like check emails and all that, but standard-size videos, for example, drag my computer to a crawl and everything becomes unbearably choppy. On top of that, even scrolling quickly causes a bit of lag. It's really strange... I'm thinking that there's probably some sort of extension I could put in the Xorg.conf device section that'll clean this up, but I haven't found anything. Any way I could clean this up?

I'm fine with using either the proprietary or open-source drivers for this. I just want things to be smooth like they were with my nVidia card.

Oh, and glgears is giving me ~100-200 FPS.....

---

### Post by Zerp64 on 2009-09-29
Nuthin' eh? Yeah, didn't think so...

Just to update everyone, I've now fully moved back to Windows XP. I *HATE* it but I don't have much choice. Even worse than that, I've noticed that Windows XP is a giant resource hog when compared to Ubuntu. Either that, or the software available for Windows is just terrible... I can't play 720p files smoothly on Windows (they played very smoothly on Ubuntu with my older, crappier video card), nor can I use my favorite video player (I used Xine, now I'm using VLC.. it just doesn't compare...)

On a very small upside though, I can numb my mind for hours on end playing Freelancer now.

But hey, if any of you guys have found a way to get ATI drivers working smoothly on Ubuntu/Sabayon/OpenSUSE/whatever, I will remove Windows so freaking fast it'll leave a burn mark on my HD...

---

