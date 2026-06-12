---
title: "Toshiba Mic Laptop Skype Problem"
date: 2008-05-03
forum: Hardware
---

### Post by alukaris on 2008-05-03
Hi.

New user to Ubuntu and I'm very impressed. I migrated from Windows to Mac about 4 years ago and now I've taken the plunge and moved to Linux. I'm very impressed with this amazing OS and I've managed to get quite a few things working but I can't get my microphone to work with Skype and was wondering if I was just missing the obvious.

My laptop is a Toshiba U300-FA3 Satellite (Canada). I'm running the latest skype from medibuntu and Ubuntu 8.04. I'm receiving video and sound and broadcasting video but not sound. The U300 is listed as a fully supported machine for this OS on the Ubuntu website, but I can't get the mic to work in any program including Sound Recorder. Anyone got this working yet?

---

### Post by oserdavid on 2008-05-03
> **alukaris said:**
> Hi.

New user to Ubuntu and I'm very impressed. I migrated from Windows to Mac about 4 years ago and now I've taken the plunge and moved to Linux. I'm very impressed with this amazing OS and I've managed to get quite a few things working but I can't get my microphone to work with Skype and was wondering if I was just missing the obvious.

My laptop is a Toshiba U300-FA3 Satellite (Canada). I'm running the latest skype from medibuntu and Ubuntu 8.04. I'm receiving video and sound and broadcasting video but not sound. The U300 is listed as a fully supported machine for this OS on the Ubuntu website, but I can't get the mic to work in any program including Sound Recorder. Anyone got this working yet?

[SIZE="2"][/SIZE]I have exactly the same problem with my new Tosh laptop with Realtek High Def Audio. So, it seems have a lot of others with their sound cards. I've tried all the solutions I can find in other places on these forums - but none work for me. Maybe I just don't know how to implement them properly. Fine sound output - but no mic detected. Neither in Skype, nor Sound Recorder. It's a real shame, because so much more works well in 8.04 - it's almost a day-to-day usable OS, almost... But this sound issue is a real show stopper. Why should people be expected to mess around with workarounds, anyway? I know it is an open source cooperative exercise, but that is no excuse for being second-rate. If it is ever to break out of the hobbyist quarter, such simple things as mass-market sound card detection should work out of the box. Bah!

---

### Post by kaunofrantas on 2008-05-04
same problem here - i have toshiba satellite M200 and microphon is not working. same as other posters i have tried suggestions in forums but it did not help.

i have filed a bug on launchpad.net already. how long does it take for someone to fix those things?

---

### Post by geekyredneck on 2008-05-12
Mark another one up for the no mic thing. I switched to ubuntu after putting up with vista for far too long and LOVE linux, my flavor of choice is pretty obvious. Easy to install fairly easy to configure. 

I have a satellite a135-s2276. and I used a workaround I found elsewhere on this forum to fix the fact that I started with no sound at all. (I can live with the speakers on the laptop not muting when i plug my headphones in.) Now hoping to be able to use skype, teamspeak, or ventrillo. (Not even sound recorder hears a thing) Not sure why this doesn't work but if anyone has any solutions to fix the mic problem it would be greatly appreciated. now I guess I have the time I will see if recompiling the kernel  helps or not. If anybody finds anything please keep us posted.

laptop specs 
satellite a135-2276 
ubuntu 7.10
using the =3stack workaround for the sound 
soundcard (according to lspci)
Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)


If more information is needed please let me know and I will post anything needed.

---

### Post by giorgios on 2008-05-27
I have a Toshiba Satellite U300-150 with Ubuntu 8.04 (Hardy Heron) 64 bit installed. Everything, apart from the front mic, worked out of the box. To get the front mic working I installed the linux-backports-modules-2.6.24-17-generic package. I got the fix from the following website: [http://www.itopen.it/2007/11/22/ubuntu-linux-toshiba-satellite-u300/]("http://www.itopen.it/2007/11/22/ubuntu-linux-toshiba-satellite-u300/")

---

### Post by oserdavid on 2008-06-04
Right! I can get Skype (and Sound Recorder) mic working. But it ceases to work every time I reboot. In my admitted ignorance, I seem to have narrowed it down to the Volume Control application. 

I need to set my Volume Control Options tab to Mic Mic to get the mic to work in Skype (and Sound Recorder). However, on rebooting, while Volume Control Options Tab says it has stayed there, the mic no longer works. I need to reset it to Front Mic, Front Mic, hear a dreadful hissing noise, then reset it back to Mic Mic, hear a dreadful (but more hopeful) feedback howl, reduce one of the Mic sliders in ALSA mixer to just below howl audibility, and - hey presto! It's working again.

Why do I need to keep resetting this Volume Control Options tab to what it claims it is on in the first place.

(And why do we need to be experts in sound control functions in order to get our OS to 'Just Work'- sorry, that's a rhetorical philosophical question)

Using Ubuntu 8.04 (i386) latest updates applied.
David

---

### Post by SolidCube on 2008-06-12
"(And why do we need to be experts in sound control functions in order to get our OS to 'Just Work'- sorry, that's a rhetorical philosophical question)"

OSerDavid: Yes, it's despicable.  After you've donated so much of your time to helping others, and so much of your money to opensource causes, for you to be exposed to a terrible barnburning bug like this one.

---

### Post by oserdavid on 2008-06-12
Yes - you are absolutely right SolidCube - and I apologise to all the hardworking volunteers who made Linux at least three-quarters the way accessible, for free, to the rest of us. However, there is an issue - that Ubuntu - even in its current incarnation - is really still not a product for people outside of the charmed circle of enthusiasts and hobbyists. However, it is clear that it is getting at least part way there - and I remain interested enough to have installed it properly in dual-boot tandem with Vista.

Still wish I could permanently solve my mic issue, however.

---

