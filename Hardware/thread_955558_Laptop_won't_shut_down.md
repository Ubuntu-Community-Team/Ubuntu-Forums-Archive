---
title: "Laptop won't shut down"
date: 2008-10-22
forum: Hardware
---

### Post by AudioDef on 2008-10-22
My Ubuntu laptop (fresh install) won't shut down. The last time I tried it seemed to have unloaded the OS but then it stops and the laptop remains powered on with a blank screen. 

Does anyone know about this and how to fix it?

---

### Post by AudioDef on 2008-10-24
This laptop I have Ubuntu installed on won't even restart. Can anyone tell me what needs to be fixed? I haven't done anything funky - it's still pretty much a fresh install. 

Also - this might help - how do I get Ubuntu to be verbose on startup and shutdown (all the yadda yadda scrolling by instead of a blank screen all the way to the login screen)?

---

### Post by mikjp on 2008-10-24
We cannot help you unless you give the specs of your laptop. 

You might also try yourselft to google for the name of your laptop + "ubuntu cannot shutdown".

> Also - this might help - how do I get Ubuntu to be verbose on startup and shutdown (all the yadda yadda scrolling by instead of a blank screen all the way to the login screen)?

You have to edit the file /boot/grub/menu.lst. Add the option nosplash to the kernel.

---

### Post by AudioDef on 2008-10-24
There's another thread [here]("http://ubuntuforums.org/showthread.php?t=347601"). Basically, add acpi=force to your kernel lines in /boot/grub/menu.lst. You can remove the "quiet" also, for more info.

---

### Post by AudioDef on 2008-10-24
I spoke too soon. It seems that adding acpi=force to the kernel line does not help with shutdown, although the last time I restarted it did so successfully. 

This is a serious bug and I'm hoping to find a solution. As much as I like Ubuntu, this will make me install something else. I often initiate a shutdown and walk away and I do not want to come back 2 hours later to find that the machine is still powered on. 

This laptop is a Gateway M305CRV. I bought it in several years ago. 

So, any help will earn copious thanks! :popcorn:

---

### Post by bonestonne on 2008-11-01
actually, funny that you mention the issue. i had the same issue yesterday but i found a fix that worked for me.

it's annoying as hell, but you'll need to have Windows installed for this (i used XP, i'm not sure if 2k will work with this, but i don't see why not).

download and install Winphlash from Gateway's website. you can google this and find it easily (if you can't find it, PM me, i still have it on my desktop).

then download the latest BIOS update for the laptop (for me it ended up being only one revision newer). I'm guessing it was a bug in that update, because i got this laptop from the dump with a crap battery, broken hinge and no wireless card, power adapter or hard drive.

after i updated the BIOS, the problem ended. it has nothing to do with the OS, its just in the BIOS not shutting down.

and partly to hijack your thread, do you have working audio? i don't, and its biting me because i'm a DJ, and a P3 thinkpad isn't going to hold up much longer.

---

### Post by AudioDef on 2008-11-02
That'd be one way to do it. I think my laptop has its latest BIOS, though. However, I recently applied all available updates through Synaptic, and added some other laptop packages, and it seems to shut down all the way now. 

Yeah, I have working audio on an Ubuntu laptop and an Ubuntu Studio desktop. Both use ALSA. What kind of sound card do you have? What does lspci say? Also, there are backports that can help with audio.

---

### Post by bonestonne on 2008-11-02
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
02:04.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
```

that's what i get out of lspci. the audio is supposedly AC'97, but so far no matter what i do, i can't get audio from the speakers or headphone out.

i'll have a check at what the BIOS has as soon as i can reboot.

---

### Post by AudioDef on 2008-11-02
I know you need AC97 in the kernel. On a Gentoo system, it's easy to find and tick off, and just recompile the kernel, then follow the ALSA howto. I just read somewhere that you CAN tweak the kernel in Ubuntu but that you'd not be able to get "official" support. I don't know how, though, since I haven't tweaked a kernel under Ubuntu yet. 

Hm... if you have the Synaptic package manager, try searching for "ac97" or maybe "ac" and "97", "audio", stuff like that. There's got to be a backport that will help. The AC97 controller is very common.

---

### Post by bonestonne on 2008-11-09
i kept poking around, but i couldn't find anything.

if you opened up your Sound preferences, what device is configured as your output? maybe i just can't find the right option.

---

