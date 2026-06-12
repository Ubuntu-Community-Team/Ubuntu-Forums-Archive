---
title: "Switched to linux, No sound"
date: 2008-09-21
forum: Hardware
---

### Post by innermeansclash on 2008-09-21
Hey, i have a Gateway 3040 gz and just set up ubuntu (first time with linux, rejoice) i originally installed just to get files off my windows op, but i like this so much i'm going to stay, if i get sound to work!

the hardware test fails the sound, and yes everything is hooked up and not muted, and i ran the lspci and got:

rick@rick-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:08.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
rick@rick-laptop:~$



can someone help fix? i can't find any soundmax linux drivers online, i tried a bunch of searches and i didnt see it on alsa.

let me know any other information needed

thank you,
innermeans

---

### Post by pieoncar on 2008-09-21
Elaborate on "the hardware test fails the sound".

You said your hardware is unmuted, have you tried running alsamixer from a terminal and making sure the software is unmuted?

You might want to try using the Intel AC'97 Audio Controller, which is probably your onboard audio jack.

---

### Post by tuxxy on 2008-09-21
Try running the test file using ALSA as the output, also you could try this command

```
aplay /usr/share/sounds/startup.wav
```

---

### Post by lisati on 2008-09-21
When I installed Ubuntu 7.04 on my laptop I had no sound, installing the system updates got it going again. Other versions need a few different "tweaks".

---

### Post by Bucky Ball on 2008-09-21
> I needed to go into alsamixer and turn the External Amplifier off, everything came on instantly then.Don't know if any help but found this for that card in another forum. Double click your speaker icon to get there. Under file it will allow you to change device. Make sure it is this one:

Intel 82801DB-ICH4 (Alsa Mixer)

That should be listed there. In switches, unmute everything (External Amplifier, as mentioned). Let us know how it went.

---

### Post by chongzivalve0809 on 2008-09-22
a professional [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) China manufactuer and supplier,established in 1983The main product is:cast steel [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm),forged steel gate valve ,pressure seal gate valve,plate [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm).  BFV Valve also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT .[gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) manufacturer website:[www.valvesupplier.net/forged-steel-gate-valves.htm](http://www.valvesupplier.net/forged-steel-gate-valves.htm)

---

### Post by innermeansclash on 2008-09-23
> **pieoncar said:**
> Elaborate on "the hardware test fails the sound".

You said your hardware is unmuted, have you tried running alsamixer from a terminal and making sure the software is unmuted?

You might want to try using the Intel AC'97 Audio Controller, which is probably your onboard audio jack.



the hardware test plays a sound and says

Testing detected sound card:
I82801DBICH4
Did you hear a sound?

but no sound is heard, that's what i mean by failing the hardware test..

i know how to get to alsamixer, but i dont know what you mean by from a terminal to see if the software is unmuted. i'll try the controler and update...

---

### Post by innermeansclash on 2008-09-23
> **tuxxy said:**
> Try running the test file using ALSA as the output, also you could try this command

```
aplay /usr/share/sounds/startup.wav
```


like i said, i'm new so i dont now how to run it with a different output :confused: but i tried that command and nothing came out... i know the speakers work bc i was just using them on my windows before i accidently deleted a wpakill file... oops...

---

### Post by innermeansclash on 2008-09-23
> **Bucky Ball said:**
> Don't know if any help but found this for that card in another forum. Double click your speaker icon to get there. Under file it will allow you to change device. Make sure it is this one:

Intel 82801DB-ICH4 (Alsa Mixer)

That should be listed there. In switches, unmute everything (External Amplifier, as mentioned). Let us know how it went.

thank you thank you thank you, drinks all around! with your unmuting the external amplifier business, and someone elses aplay /usr/share/sounds/startup.wav i fixed it right quick... to quote a n00b... w00t w00t... you guys pwned this gateway!

---

### Post by Bucky Ball on 2008-09-23
Good news! Don't forget to mark your thread as solved from 'Thread Tools' so others can surf here to fix their sound prob.

Rock on :guitar:

ps: and post again with any more ](*,)

---

### Post by chaime on 2008-09-24
I just wanted to clarify something. I have a Gateway 7322GZ with the same soundcard (ICH4 - AC'97). I tried EVERYTHING to get this sound card to work before finally I came to this post...I had even tried compiling the newest ALSA, then reverting to the Debian kernel ALSA, etc., ad nauseam. I was about ready to give up before I saw the comment about turning the external amplifier OFF.

I would have never imagined that. I kept trying to make sure everything was ON. And it *appears* someone got this mixed up during this thread. The external amplifier in the alsamixer shell application is the one all the way to the far right, and at least for my Gateway, in order for the sound to work, it must be MUTED, i.e., OFF.

Thanks a million to whoever figured that out.

Chaim

---

### Post by coreychch on 2008-09-27
Hey all, thought I'd tack a relevant question on the end of this thread... First time Linux user, and I have just installed Ubuntu 7.10 onto a computer that was using windows.  The Soundblaster Awe64 Gold soundcard isn't being detected (though it worked well on windows).  I ran that lspci command in the terminal and no multimedia devices came up at all.  

I have read around lots, trying to solve this problem, do I need to install a modem into this machine and download some updates?  Will that help?  

Or can I download updates separately and transfer them to the other machine?  

Is it likely I will find a solution or should I quite before I waste lots of time and get frustrated further?

Thanks, really appreciate your help.  This is a bummer as I intended to use the computer for music.

---

### Post by Bucky Ball on 2008-09-27
Yes, you need a modem. Ubuntu is fairly net dependent (in some circumstances). You would be better off posting this in a new thread. No one will find you here.

---

