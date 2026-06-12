---
title: "Ubuntu on Zepto Notus A12 Mobility."
date: 2009-01-21
forum: Hardware
---

### Post by casbahdk on 2009-01-21
I have just purchased a Zepto Notus A12 Mobility on sale and am planning ahead for when I receive the computer. My choice of OS will of course be some flavor of Ubuntu, maybe Xubuntu or Ubuntu with LXDE.

Zepto's homepage states that - Zepto Notus has been tested to ensure that it works with Ubuntu, and that "Ubuntu Hardy Heron 8.04 has driver support for compatibility with the most used hardware." The Zepto Notus has the following:

Monitor 
12.1” WXGA (1280 x 800) 
Processor 
Intel® A110 Processor 800MHz, 
512KB Cache, FSB 400MHz 
Chipset 
Intel® 945GU + ICH-7U 
Memory 
1GB DDR2 667MHz RAM SO-DIMM, 
Max. 1GB

80GB 4200rpm ATA Hard Drive 

Graphics 
Intel® Graphics Media Accelerator 950 
224MB shared memory 

Sound 
Realtek® ALC262 High De&#64257;nition sound quality 
Microphone ind og headphone out 
1x Stereo 1,0W speaker 

Connections 
1x RJ-45 jack 
1x RJ-11 jack 
3x USB 2.0 
1x RGB; VGA port, 15pins 
1x PCMCIA Card Slot 
1x Digital audio (S/PDIF) 
4-in-1 Card reader (SD/MS/MS Pro/MMC), 

Network 
Internal modem - V.92/56K bps 
Realtek®  10/100/1000  Mbit LAN 
Built-In wireless LAN 802.11 a/g/n 
Built-In Bluetooth 2.0 

There is no CD/DVD drive so, I will have to figure out how to get Ubuntu onto a USB pen drive. Do the graphics, sound, connections and network look like they will work? There should be enough memory, right?

Cheers,

Brian

---

### Post by betonarbejder on 2009-01-21
I have installed Kubuntu 8.10 from a USB cd-drive on my friends Notus A12.

Zepto does not provide any Linux documentation.

He is happy running on it and It is supposed to be more quiet when running Linux than the preinstalled Vista. He does however also tell that Kubuntu twice has suddenly returned to the login screen without notice - I assume that X has crashed.

I think Kubuntu 8.10/KDE4 runs smoothly but it is easily loaded so much that the fan gets noisy.

Sound (through headphones - speakers are mute so far), network, graphics, USB works. Suspend to RAM works quickly as well but when returning from suspend to RAM the computer seems unable to connect to wireless networks, though many networks can be seen in knetworkmanager. This might be caused by knetworkmanager - It seems a bit unstable to me on my T400 as well.

The RAM seems to be sufficient.

I have not been able to access the programmable P1 and ECO buttons, and with xev or getscancodes I am not even able to get the scancodes...

Johannes

---

### Post by casbahdk on 2009-01-21
Thanks for the prompt reply Johannes,

Have you come across any third party info about the issues your friend is experiencing with the Zepto Notus? Do you think there is any chance of getting Compiz to work on the Notus, maybe with GNOME or a lighter window manager? How does his video work?

Cheers,

Brian

---

### Post by betonarbejder on 2009-01-21
Hi

No I have not yet looked into the crashes, but I did just experience it myself now before he left with the machine. Just before X returned I saw something similar to the list of that which appears when shutting down (k)ubuntu. That list might have been connected to X starting... or KDE shutting down more or less controlled. At some point I will look at his machine again, but he has experienced the thing twice in the 2-3 month that he has had it (kubuntu only) and he is content.

I would think that compiz would work since KDE4 works fine and smoothly with its build-in desktop effects enabled (compositing effects mostly identical to those of compiz).

---

### Post by casbahdk on 2009-01-29
Here is something I came across that may help on the sound issue. The Notus A12 also uses the Realtek ALC262 sound card. Let me know if it works, it is in my own best interest :-) I still haven't received my A12 and a week has almost gone by since I ordered it and Zepto confirmed :-(

[http://ubuntuforums.org/showthread.php?t=823694]("http://ubuntuforums.org/showthread.php?t=823694")

---

