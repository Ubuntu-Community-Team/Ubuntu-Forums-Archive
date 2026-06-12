---
title: "Upgrading RAM - ubuntu stop working"
date: 2015-05-11
forum: Hardware
---

### Post by rajko2 on 2015-05-11
Hello,


I have a problem and I hope that anyone can help. Recently I upgraded the RAM on a laptop from 2x1G to 2x2G. Now I have a problem that Ubunto no longer works,
only half of screen is working and performance is very very slow.I have a dual boot with windows8.1 and win works fine. If I remove any of the stick linux also 
works fine, only when is back to 2G of RAM. I did memcheck of RAM and all sticks passed. It seems that Linux does not automatically upgrade to the "new RAM". 
Do I need to reinstall ubuntu? Or is there some other option?




specifications:
Version of Ubuntu 14.04.2 LTS
Processor: Intel Mobile Core 2 Duo T7300
RAM: 2x2G DDR2 PC2-6400
Graphics: ATI Mobility Radeon HD 2400

[COLOR=#333333][FONT=Ubuntu] dmidecode output if that helps: 
[/FONT][/COLOR]

---

### Post by dino99 on 2015-05-11
ram upgrading can be very sensitive in some cases: better to set the same brand, model. Check first the bios : is the ram upgrade well recognized, using the right voltage and latency, .... (recheck the ram specs)
sometimes switching the ram sticks (inverting plots) can be enough to get good results (but as windows run fine after upgrading, then it sould not be needed)

note: i'm also using some ddr2 sticks, and one of my system was having kernel panics while booting, and finally discovered that the default bios ram setting set on 'auto' in fact was not picking the '1.8 v' that ddr2 usually needs, but a lower voltage, so the boot panic. Setting it the 1.8 v manually resolved my issues

---

### Post by rajko2 on 2015-05-11
Thanks for the reply. But in BIOS I do not have any option to change the voltage/latency or, I can not find it. I have an AMI BIOS version 1000B70001 and only 
what I see is that I have 4 gigs of ram...  If I go in linux in tty type (free) also show 4g of ram. :)  and the sticks of RAM are identical. 


Here is the CPU-Z from windows:

 [[IMG]http://shrani.si/t/3N/oW/2FjlJZT8/cpu.jpg[/IMG]]("http://shrani.si/?3N/oW/2FjlJZT8/cpu.png")

---

### Post by dino99 on 2015-05-11
i cant check my own AMI bios here, but if i remember, ram settings are inside the 'Advanced' tab, then the settings are only viewable IF you (temporarly) dont let the cpu on 'auto' about its freq.
the fact that the bios is seeing the 4 gb is a good news

---

### Post by mattharris4 on 2015-05-11
This is a weird problem.  I increased the RAM on my desktop and Linux (Edubuntu) recognized it right away.  Of course I copied the specs off of one of the old RAM sticks, researched compatibility online and made sure the replacements were of the same specs (other than the capacity which was higher).  Some computers can only recognize 2GB RAM (some very old computers) but that still does not explain why the computer is acting like yours is, in most cases assuming the RAM is of the proper specs the computer would recognize the maximum and still function fine.  Also, the Core 2 CPU should recognize 3.2GB if 32 bit and as much as you can get in it if 64 bit.  Other components in the motherboard may not, however (but in this case it should, the processor is 64 bit and any computer manufacturer worth their computer chips would mate it with a mobo capable of running at least 4GB RAM).  I do have a few suggestions, listed below.

1.  Remove and reinstall the RAM sticks.  If one or more sticks isn't making good contact with the contacts in the motherboard all sorts of weird things can happen.

2.  Research your specific computer model check the specs of the RAM that came with it.  If your RAM isn't the same (except for the capacity), get RAM that is.  Incompatible RAM will sometimes fit into the slots on a computer.  In my case my desktop takes DDR2 533MHz DDR-4200 or DDR2 667MHz DDR-5300 RAM.  800 MHz PC2-6300 will fit but is not guaranteed to function in my computer (granted I haven't tried it).  My understanding is most non-server computers (i.e. computers made for home use) need non-ECC RAM, ECC RAM will not work (and will have a different DDR or PC2 number, it may or may not fit in the slots on the mobo).

3.  A quick check of the CPU tells me that it is 64 bit.  You should not be having an issue with your computer recognizing 4GB of RAM unless somehow it was installed on a motherboard that only can handle 2GB of RAM -- highly unlikely.  Recheck following step 2 and make sure you have the appropriate RAM for your computer

4.  If all else fails, reinstall Ubuntu -- taking care to copy your documents, pictures, music, videos, etc. to a portable hard drive or large capacity USB stick.  This is a last-resort step as it may involve reinstalling Windows as well.

---

