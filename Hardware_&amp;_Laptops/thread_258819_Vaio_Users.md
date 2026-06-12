---
title: "Vaio Users"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by Kanybus on 2006-09-16
It seems that we have the most problems configuring our machines to Ubuntu... or any Linux for that matter :)  I'm relativly new to Ubuntu and Linux so maybe we could use this thread (maybe it can get stickied) to post our machines, what problems we had and how we over came them.  Or if this thread is already active some where, some one could be kind enough to link it.  I am using the PCG-K33 and am still trying to configure it on my spare time lol
Problems thus far: I'm Linux/Ubuntu illiterate lol

---

### Post by Chemroydal Tissue on 2006-09-16
My ex-wife has a Sony VAIO PCG-FR130 with a Hawking HWC54D (rt2500 chipset) PCMCIA card plugged in. No problems on a fresh install (100% Ubuntu), with the exception of the dial-up modem, which will most likely never be used. It was, honestly, the second-easiest Ubuntu installation I've done. The only other minor detail I can think of was that my ex-wife couldn't get the ethernet card to work at a local library (where she works). She waved over the head of the IT department, who fixed it easily - I'm not sure what he did, since I wasn't there, and she doesn't know enough to tell me. If anyone has a similar problem, PM me and I'll figure out what the solution was.

---

### Post by Kanybus on 2006-09-16
I haven't run into too many problems, just trying to configure and customize it with all the laptop options like the fn keys.

---

### Post by NikoC on 2006-09-17
Sony Vaio vgn-s4hp: no suspend or hibernate, hangs on shutdown, takes very long too reboot. No solutions found yet...

---

### Post by trcook on 2006-09-20
I am on a PCG-R505GCP. The install was a breeze, the hardware setup was uninvolved and the performance has been pretty good so far. I am running the latest Dapper release of Kubuntu. The big problem I'm having now is configuring the touch pad. It works very well (all the features such as border scrolling and tap to click are working -- even the jog dial for vertical scrolling!) but when I try to customize it - primarily to turn off tap clicking, i can't seem to get anywhere. none of the gui programs are working for this and i can't seem to alter functionality by altering xorg.conf directly. I've also switched drivers all over the place from the ubuntu provided drivers to the current 14.4 version of the synaptic touch pad drivers. I can't seem to find seperate ALPS drivers. Outside of that one thing though, everything has worked very well:)

---

### Post by NikoC on 2006-09-21
Perhaps this is also an interesting forum topic since no solution has been found yet ...
[http://www.ubuntuforums.org/showthread.php?t=212270]("http://www.ubuntuforums.org/showthread.php?t=212270")

---

### Post by viper on 2006-09-22
PCG-FR820 here, Last year installed Kubuntu, mostly went without hitch 
(dual boot XP) had some minor issues with the touch pad and wireless but overcame most dramas for a while then i started messing with things and broke the GUI (you name it i broke it!!) Begining of this year nstaled Ubuntu and have not had a problem except for the internal modem, no matter what i try just cant get it to work#-o , when we travel i need to be online and some places dont have broadband only dailup. So if any one has gotten their head around this problem i would like to know if its only the Sony Vaio`s.

---

### Post by mstrat on 2006-09-22
So far, I have installed Ubuntu on a Sony Vaio and a Toshiba Satellite...good thing I started with the Sony, the Toshiba has screen resolution issues that I finally found a slight satisfaction with, and still have no sound...I use my Sony more even though it is an older, slower machine, it has sound and proper screen resolution.

---

### Post by tonec on 2006-09-26
I have a vaio pcg lek-z600 
i think the problem with installing on a vaio may be for users with the external cd drive , such as me ! 
I have added the line 
ide2=0x180,0x386 at the boot prompt 
but is still hangs on the installing hardware dirvers part of the install going to a infinite loop of 
port 1 disabled by hub (emi?) 
I am pulling my hair out on this , has anyone managed to install on a vaio with an external cd drive ?
thanks

---

### Post by jko21 on 2006-09-27
Hi

I have a Sony VAIO VGN-FE21M.

I installed ubuntu 6.0.6 without any problems.

Works:
The touchpad, nvidia graphic card, the screen resolution, acpi, super multi dvd, the shortcut keys for the sound (mute,volume-,volume), brightness changes only with smartdimmer. The second cpu needs smp kernel to work and then to change the frequency in gnome cpu frequency scaling monitor you need these commands : 
# apt-get install cpufrequtils
# cd /usr/bin
# mv cpufreq-selector cpufreq-selector.bck
# cp cpufreq-set cpufreq-selector
# chmod u+s cpufreq-selector
Everything that is not in the list below

Doesn't works:
The shortcut keys s1-s2, fn keys, motion eye camera, hibernate, bluetooth (it connects with my mobile phone, but it needs a password to trasfer files:confused: ) 

Haven't try:
Suspend, modem, wlan, memory card adapter, external monitor

---

### Post by irsic on 2006-09-27
I have VGN-B3VP. Installation was quite ok, but it seems I have constant problems with video & sound. Once I worked out why my sound isn't working (which now works fine), there came the problem with video. Though I suspect it isn't problem with ubuntu this time. It could be the totem movie player. I get the sound but can't the picture of .avi files.

---

### Post by tonec on 2006-09-27
yes this has an internal cd rom right ? 
I think the problem with vaio's is with an * external * cd rom which the smaller 12" screen ones have , which is my model the pcg lek-600 , I am still having hangs when it gets to detetecting hardware drivers . it goes into a loop 
port 1 disabled by hub (emi?)
e-enabling config failed can't read hub descriptor
at the stage of detecting hardware drivers ... :confused: ](*,) 
anyone out there help ? 
thanks

---

### Post by wieman01 on 2006-09-27
Sony Vaio VGN-270... 

_Everything fine including:_
1.  Wide-screen
2.  Sound
3.  Bluetooth
4.  Modem
5.  Wireless (WPA1, WPA2)
6.  Ethernet
7.  Touchpad
8.  External projector (Xinerama)
9.  DVD-Writer (K3B)
10. Mute & brightness buttons

_Have not tried:_
1. PCMCIA
2. Dual Reader
3. Suspend

_Does not work:_
1. Volume buttons

---

### Post by Kateikyoushi on 2006-10-02
I use a VAIO X505 everything works with edgy hibernate, suspend, Fn keys worked with the previous kernel so I bet it will work in the final version.

Have a TR5 which has no linux driver for the webcam so that stays with XP.

I would install ubuntu on the U101 if the thumbkeys would work, does the sonykey driver support it ?

---

### Post by tonec on 2006-10-02
hi
I had extensive trouble trying to get any linux distro installed on my vaio pcg lek-600 ( with external pcmcia cd drive ) 
I finally tried using xubuntu which installed without any bother ! 
so give this distro a try if youre having problems with the standard ubuntu install ... it comes with synaptic so anything you need to insall that may be missing is a synch to install ...

---

### Post by schegi on 2006-11-07
To tonec

In my opinion it has something to do with pccard the ide/pcmcia? manager. It somehow detects the pcmcia-cdrom as a normal pcmciacard and resets the settings from before (ide2=0x180,0x386), so the installer can´t find your cdrom any more.
I have the same problem but not solved jet.

---

### Post by tonec on 2006-11-07
hi 
i got round this by installing xubuntu - this installed ok , it still foes into this loop when you boot up but only for 10 seconds or so and then kicks itself off it ... 
which I can deal with - give xubuntu a go ...
hope this helps

---

### Post by schegi on 2006-11-08
Yeah i worked around by installing a older version cause i have already had experience with debian on this notebook, and now i upgrade my system.

---

### Post by bluefrog on 2006-11-23
VAIO VGN-FS215E

FN keys never worked but well not a big deal...

Since Edgy, cdrom and wifi cannot be recognized at the same time

acpi on = wifi but no cdrom
acpi off = cdrom but no wifi

bug filed against acpi as I think it comes from there...

---

### Post by NikoC on 2006-11-24
Today I tried the Freespire LiveCD and my vgn-s4hp shutted down without any problems what so ever... I wonder what those guys at Freespire did to make it work...

---

### Post by MrZammler on 2006-12-15
Hi,

I'm trying to install xubuntu 6.10 on a Z600LEK

Well, it boots after setting ide2=0x180,0x386 but then hangs with ide timeouts on hde (the external cdrom)...

Anyone could offer a tip on how to get it going? Does it need any more extra kernel parameters?

Thanks

---

### Post by MrZammler on 2006-12-23
I think at some point, it sends a reset command to the pcmcia (i see the cdrom power light turn off and then on) and at that point the boot stops.

I've tried "nopcmcia" in kernel parameters, but it doesnt make any difference...

any ideas?

---

### Post by z3r0k00l on 2007-02-15
ive got a VGN-FE21M, ive gotten the webcam and wireless to work by installing the drivers manually...

the smartdimmer seems to freeze the screen when i try to query the current screen brightness level... 

um, i dont know what else to try, the modem shows up in the networking dialog box, but its inactive, and i dont really need it for anything..

the mute/unmute key works, but the volume +- and the S1 S2 keys dont work either..

the pad works fine, and so far im liking it. specially after i got the ipw3945 installed for the wireless... took me all afternoon :guitar:

---

### Post by NikoC on 2007-02-20
Just tried development Feisty Herd 3 and I have to say I'm impressed: problems with suspend and shutdown on my VGN-S4HP are gone, i.e. it works! Shortcuts on my keyboard are functioning also! Only now I 'm still struggling a bit with external monitor setup!

---

### Post by sopolev on 2007-06-05
Had good luck with Xubuntu and Ubuntu Feisty on my PCG-XG18. Initial issue was something in the BIOS kept the installer from running - reset it to default settings and it worked - no installer hang. I narrowed it down to the CPU scaling, so that stays with default settings.

Works:
PCMCIA wireless card (3com crpag175 a/b/g xjack)
USB with LAN adapter (fairly new netgear 10/100 - forget which one)
Video at 1024x768 ONLY. That is the highest afailable, so that's ok.(neomagic)
Jog dial (scrolling/clicking only - need software to do anything else)

sort-of/Mostly works:
Alps touchpad - too sensitive, can't adjust or disable. tried everything I've found here
DVD-ROM - reads CDs fine, but won't mount DVD media (says no media in drive)
Suspends, but network unavailable on resume until reboot.

I'd really like to get my touchpad to configure. I can live without suspend and I'll probably figure out the DVD, but the inadvertent clicking makes me nuts.

---

### Post by crunchmatic on 2007-06-06
I have a PCG-SRX87 Notebook with an external dvd drive. The first linux distro I've been able to install is SAM Linux 2007 based on PCLOS.

I don't know if Ubuntu has this, but SAM Linux will boot from USB Flash memory after you copy all the files from the cdrom iso disk to the USB Flash Memory. You still boot from the cdrom, but during the boot process if the files are detected on the USB Flash, then it continues the boot from there (my Vaio cannot boot directly from USB).

Most devices work (i.e. wireless, touchpad, audio) but I haven't tried everything.

Hope this helps.

---

### Post by bcoutinho on 2007-06-06
Sony Vaio VGN-N230N
Ubuntu 7.04

Everything working but:

- Fn-keys
- Front speakers do not mute when headphones are plugged (I can force it to mute with Gnome ALSA Mixer)
- External video worked (with a patched i810switch), but with wrong resolution and synch frequency. Chipset Intel 945GM

I haven't found solutions for those issues yet.

What I haven't tried: SD card, memory stick, modem, firewire.

---

### Post by IntuitiveNipple on 2007-06-06
In case you haven't seen the thread [Calling All Vaio Owners]("http://ubuntuforums.org/showthread.php?t=465491") you might be interested in the work we're doing to enable the custom capabilities of many Vaio portable models via the sony-laptop kernel driver. We're aiming to solve the issues of non-working Fn-keys, bluetooth and WiFi radio power, and more.

Please take a look and see if you can help us.

---

### Post by Redrazor39 on 2008-01-27
I have a relatively new VGN-SZ430N and I can't get the motion eye camera, mic, or fingerprint reader to work (I can't find software for the fingerprint reader that has protector suite QL on Vista) and I can't find any driver or w/e to make the camera work. I dual boot Vista and Ubuntu; I'm so glad I kept Vista. There are ABSOLUTELY NO PROBLEMS on Vista, but these things just bother me on ubuntu!:mad::(:twisted::evil:[-(

---

### Post by kayel_justice on 2008-03-30
Other than the learning curve to use ubuntu, once you understand everything vaio users have the least problems I think. But you are right, our parts our foreign so we have to look harder. I have 7.10 gutsy, on my nr110-e vaio. And man IT IS SWEET

---

