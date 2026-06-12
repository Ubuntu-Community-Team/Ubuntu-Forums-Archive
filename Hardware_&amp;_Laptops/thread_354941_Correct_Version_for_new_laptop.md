---
title: "Correct Version for new laptop"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by VMan on 2007-02-06
I'm interested in Ubuntu because I have heard that it handles multi-media better than some of the other distros.

I just got a new laptop and am looking at the Ubuntu distro.  I'm not a total newbie (been running linux since the mid 90's; and this is the 3rd laptop for linux).  I have been using Mandrake since around V6.  Before that I ran Caldera and Redhat on various systems.  All of my experience is on computers that would be considered ancient/obsolete.  I haven't tried a new OS since Mandrake 10.1 if that gives you any idea.  This laptop will be my main computer.  The only real loads I put on it will be video editing and graphics.  Open Office doesn't count as much of a load.  The old linux computer will be put to use as a file server for both windows and linux based computers.

New laptop specs:
Toshiba Satellite A35-S4467
CPU: Core 2 Duo T5200 
Chipset: Mobile Intel 945GM Express
Video:  Intel Graphics Media Accelerator 950 (shared memory) from Toshiba propaganda; Device manager reports it as 945GM.
Network: Intel PRO/Wireless 3945ABG
RAM: 1G
HD: 160G SATA (also have an external Firewire/USB HD)
Optical Drive: DVD Supermulti (also have an external firewire/USB LG 5160D DVD)
Display:  15.4" widescreen 1280x800
Sound:  Realtek High Definition Audio (this is all Device manager will tell me)
Modem:  I haven't used a modem since being a beta tester for Multimedia's cable internet in the late 90's.
Other:  5-1 bridge media adaptor (would be nice if this actually worked under Ubuntu for SD cards, but is not essential); PCMCIA Type I/II card slot TI PCIxx12 CardBus Controller.
Ports:  USB & Firewire

If you need more specs to answer my questions, please respond in this thread.

Questions:
1.  I see a lot about the 64 bit OS on AMD stuff, but not on the Intel Core2Duo.  Should I use the 64 bit version with this CPU?

2.  Are there any known problems with the Intel Core2Duo that I should know about?

3.  Are there any known problems with the chipset?

4.  Are there any known problems with the video chipset or display?  

5.  I have had some interesting experiences with the sleep, hibernation, & power management modes in the past.  How is the current development on these?

6.  I plan on using the LiveDVD version to test first before doing a complete install to the HD.  Any suggestions?

7.  I have heard that the Windows Vista HD format is difficult to work with.  When I do the install, I plan on Wiping the HD, installing Ubuntu to the second partition, leaving 70G on the first partition for a reinstall of Vista (may go back to WinXP).  I have read the instructions on how to get a dual/multi boot system with Vista working.  Any suggestions?

8.  If you have any other suggestions (other than returning the laptop and getting one with better hardware; unfortunately, that is not an option) for getting Ubuntu to run, please let me know.

Thanks

Moderators:  If this is in the wrong place, forgive me and please move it.

---

### Post by LotsOfPhil on 2007-02-06
I can only answer #1, the reason it is called AMD64 is that AMD came up with it first. It should work just fine with an Intel CPU.
[http://en.wikipedia.org/wiki/AMD64#Differences_between_AMD64_and_Intel_64](http://en.wikipedia.org/wiki/AMD64#Differences_between_AMD64_and_Intel_64)

---

### Post by amgra on 2007-02-07
I have a very similar laptop as yours, I have a Dell Core Duo, Intel Wireless 3945 and Intel Video 945GM.

I do not want to scare you but I first, none of this three items were tunned correctly. I had to do some setups (hard at first) and today, I have a very powerfull Linux Install. I want to think it was hard first becuase I am very newbe to Linux, but really it is not the big deal.

Video: You do have to install 915resolution
Wireless: In server CD it is not included, but in regular Desktop CD it is working fine.
Core Duo: you have to choose a difeferent kernel in Synaptic.

Cheers, and viva Linux forever. :guitar: 

BTW I am thinking to erase completly my Windows partition, I am getting to the point of having EVERYTHING setup in Linux.

---

### Post by egress123 on 2007-03-15
Have you gotten the sound to work on this laptop?  I got the same laptop but the sound is not coming out..

---

### Post by tschneiter on 2007-03-16
Apparently running the 64 bit kernel works fine, but you may run into trouble with program compatiblity. I currently run i686-generic on my core2duo. 

I am also using the 945gm graphics chipset, and had to install 915resolution to get my screen working properly. 

I am using a dell, and had some trouble in Edgy, at first, with the sleep. It worked properly after adding "blacklist video" to a module blacklist file (dont rememebr the location off the top of my head). Hibernation takes as long as shutting down, so I dont use it. 

I recently upgraded to Feisty, and have found a great deal more support for my hardware, and everything works smoother. With Feisty, I have had easy hardware recognition, and all ACPI functions work better, out of the box. Further, temperatures under Feisty were an average of 10c lower than under Edgy.

Hope this helped a bit!

---

