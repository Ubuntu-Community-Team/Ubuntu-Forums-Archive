---
title: "Nvidia driver problem"
date: 2011-06-16
forum: Hardware
---

### Post by argybee on 2011-06-16
Hi ultra-newbie here...
10.04 on my laptop has been great and always worked well with any of the Nvidia drivers (173,current). 
I have recently tried several times to install 10.10 and 11.04. All goes well until I activate the Nvidia drivers. I then restart and end up with an unresponsive black screen after grub. 
I have tried the different versions of Nvidia drivers and have tried MANY different distros based on either 10.10 or 11.04 
If I reload a fresh 10.04 and then Nvidia drivers no problems. Upgrading from 10.04 to either 10.10 or 11.04 gets me to the same black screen problem.
I am ready to remove Win for good but will I never be able to run newer versions of Ubuntu/Linux? :(

Can someone please suggest a solution - I have been searching these forums for over a week now. Thanks in advance....

this is some hardware info...

Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
VGA compatible controller: nVidia Corporation G86 [GeForce 8600M GS] (rev a1)
Network controller: Ralink corp. RT2860
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

---

### Post by grahammechanical on 2011-06-16
I do not know if this will help but I think that the activation of Nvidia drivers over previously activated drivers causes conflicts in the configuration files. I have not had your problem. In my case any attempt to get enhanced effects working would result in dialog boxes that were frozen to the screen. In an earlier version of Ubuntu with earlier Nvidia drivers I could get enhanced effects working.

I have a separate home partition. This problem was solved when I did a fresh install which included a format of the /home partition. I backed up all my important documents first. Do not forget to do that. Although I must say I have not had this problem when going from 10.10 to 11.04.

A fresh install without formatting a separate /home partition would leave all the old configuration files in place. You could try deactivating the Nividia drivers before upgrading to 10.10 and then go on to upgrade 11.04.

Others on the forum might have a less drastic answer to this problem.

Regards.
Regards.

---

### Post by argybee on 2011-06-16
Thanks a lot for the quick reply G-M...

I have loaded and reloaded 10.10 and 11.04 many times (maybe 20) on used, reformatted, deleted, resized and brand new partitions. 
Always the same result when it comes to adding the Nvidia drivers. 
A fresh load of 10.04 (several different distros) always works fine after the Nvidia drivers are activated. 

(I would go with Linux full-time but to see such basic compatibilty 'lost' with new versions is scary):frown:

...off to try your final (drastic) suggestion....however extreme... thanks again

---

### Post by Sylos on 2011-06-16
Not that I can offer a solution but there is talk of this being a kernel bug - hence the newer versions are not working.

See here:

[http://www.nvnews.:popcorn:net/vbulletin/showthread.php?t=161994](http://www.nvnews.:popcorn:net/vbulletin/showthread.php?t=161994)

You could try rolling back to 2.6.32 kernel wich some people have found to work  - although Im not sure if there may be other undesirable results in doing this (after all - krenel updates arent just for the fun of it).

Good luck

---

### Post by argybee on 2011-06-16
Thanks Sylos...
Uh oh... 'kernel bug' is just what I didn't want to hear but after so much testing I suppose I shouldn't be surprised... makes sense.
I'm getting way too old to dig that deep so guess I might be stuck (with a little less faith?) in a 10.04 time-warp.

[btw your link is a shocker - needed google to work out what it might be! :lol:]

---

### Post by Sylos on 2011-06-17
Yeah I just tried it now - sorry about that - very poor quality link!

Hey ho. I wonder what kernel version 10.04 goes up to. If it is a kernel bug then updating 10.04 to that kernel would be expected to result in the same problem.

---

### Post by argybee on 2011-06-17
Thanks again Sylos...
I've decided to load a 10.04 Mint for a while and keep updates under control. (seems a nice sensible distro) Currently @ 2.6.32-21 with Nvidia(current) and of course all is good.
I'm out of the IT game for over ten years now but this seems like a development control issue that I would have thought not possible with the talent and methods involved....!?
I will eventually get around to doing some more tests (and followup posts) but for now must focus on other stuff.

---

