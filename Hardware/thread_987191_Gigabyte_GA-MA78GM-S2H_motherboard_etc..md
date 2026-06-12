---
title: "Gigabyte GA-MA78GM-S2H motherboard etc."
date: 2008-11-19
forum: Hardware
---

### Post by chandra on 2008-11-19
Dear Folks,

I am contemplating building a PC from the following:

Motherboard: Gigabyte GA-MA78GM-S2H with AMD 780G + SB700 Chipset, ATI Radeon HD3200 IGP, and Realtek ALC889A codec
CPU: AMD Athlon 64 X2 5200+ AM2 Dual Core
Memory: Corsair 4GB kit Twin2X PC8500 1066MHz
HDD: SATA
DVD/RW: SATA

Has anyone had experience with a similar system for Intrepid?  Have there been any problems with this configuration, especially with the BIOS, on-board graphics, sound, or SATA devices?

Many thanks.

Chandra

---

### Post by mikeeve on 2008-11-20
I just started yesterday trying to install Ubuntu 8.10 on the GA-MA790GP-DS4H motherboard. The graphics drivers do not want to install. Ubuntu can't recognize my widescreen monitor (maybe because the display driver is not installed correctly).  It even says my display is running at 0 hz! But the screen is quite readable, just the wrong resolution.  Funny, the 7-year old Win XP installed without a hitch... 

LAN and sound work.

Edit (next morning): finally got working ATI driver and correct screen resolution. I didn't take really good notes, but here is 90% of what I did:

from terminal, 
fglrxinfo 
 (responds not installed, tells me package to install)
sudo apt-get install xorg-driver-fglrx
 (required to insert 8.10 CD)
reboot

checked resolution via system/preferences/screenresolution
(resolution still wrong)

then went to system/administration/hardware drivers
(complained 2 drivers installed, asked me to activate ati driver, did so)

reboot
(screen resolution/refresh rate now correct although  system still doesn't know what monitor I have)

at least, I can move on, I think.

---

### Post by anv on 2009-01-17
I have had this: GA-MA78G-DS3H (rev. 2.x) "little brother", received today replacement for the one which I left inside to shop two weeks ago again major bios based problems. USB drives ar not able to boot, it boots system some times not every time, ps/2 working and not working, quite bad flaw from factory to give out these boards, seeking from several forums many have complained that they have returned several boards in change of those which ar not working. too bad I really liked the idea to have all AMD chips and Ati inbuilt good graphic card, this though I managed to get work with Catalyst in this second motherboard, but not the first. because I can't hook anything in booting phase to USB.s I can not try upgrading FLASH...but I don't believe it would help.  + you can burn fingers in the north bridge some say thay have had 80 -100 C

---

### Post by cygnus-X1 on 2009-01-26
I have this Mobo, Rev 2.0, and find it interesting that 8.04 has loaded differently every time I've had problems and chose to reload rather than fiddle with it. The NB isn't really very hot, just really warm. No burns though. The CPU is a 4850e which idles at 28.5C and has peaked at 34.5C. I guess that Arctic Silver 5 really works!:guitar:

At present, I'm looking at virtualization. Ubuntu host and XP3 guest. USBs *seem* to be working fine. I'll check them out when I get time.  The problem I'm having is the audio. When I load the XP into the virtual box, it cannot find the on-board audio. :confused: This board has the Realtek ALC889A codec. I haven't played/searched with it yet, but any info from anyone who's figured it out might help everyone with this board. THX!

---

### Post by Riverine on 2009-01-28
I've been running 8.10 on the GIGABYTE GA-MA78GM-S2HP with an AMD X2 5050E 2.6G for two weeks now.  

The only problem I've encounter thus far is with the integrated graphics.  I'm using the fglrx driver.  The desktop (with or without compiz) and video playback with vlc work without problem.  But some 3D games (notably Extreme Tux Racer) won't work--it looks like some sort of sync problem but I'm not sure.

I'd like to know if anyone has this board working with Mythbuntu.

---

### Post by neilevan814 on 2009-02-05
Hi cygnus-X1..just a quick question for you about the arctic silver 5 compound.  Have you ever had to actually remove a thermal pad from a new heatsink before applying the arctic silver 5 to the heat spreader of your processor?  Also, how much of the arctic silver 5 did you actually apply?  The directions for my amd 64 x2 seems to show that you use this little tiny dot in the middle of the processor, don't spread it out, and then just place the heatsink directly down and tighten.  Is this how you have proceeded?

---

### Post by cygnus-X1 on 2009-02-05
> **neilevan814 said:**
> Hi cygnus-X1..just a quick question for you about the arctic silver 5 compound.  Have you ever had to actually remove a thermal pad from a new heatsink before applying the arctic silver 5 to the heat spreader of your processor?  Also, how much of the arctic silver 5 did you actually apply?  The directions for my amd 64 x2 seems to show that you use this little tiny dot in the middle of the processor, don't spread it out, and then just place the heatsink directly down and tighten.  Is this how you have proceeded?

Hi neilevan814. Thanks for the inquiry. The heatsink didn't have a thermal pad, since I bought the retail version of the CPU from N3w3gg. So it's the stock heatsink that came with it. Bare aluminum. As such, I used the stock compound that was already spread out on the CPU when I initially put the system together on an Abit mobo. At that time it was idling at around 32-33C (90F) and pushing around 40-42C (106F) when working. Not bad for what I've been used to. Here's why. To put it in perspective, my old 2.4G P4 system is currently dying and has always run at an idle of 36-37C (98F) and would peak at 54C (129F). Now, depending if I'm rendering or not, is working at between 49C (120F) for moderate file transfers) and 59.5C (139F) when it's rendering video. Needless to say it makes a great space heater this time of year! :biggrin:

Initially I thought I was having problems with the Abit mobo, so I decided to get a different mobo, the Gigabyte. (It turned out to be the memory instead. 20/20 hind-sight! #-o) Since I was getting a new mobo, I thought it would be a good idea to get some good compound as well. Getting the old compound off wasn't very difficult. I followed the directions from the site, comparing the size of the dot of AS5 to use, (about 80% the size of a .177cal BB), and how to gently use the heatsink to spread/mash it into position, to make sure it was done correctly. (I read all about how much effort it takes to remove both the heatsink and compound after it's been on for any length of time. :shock: ) The directions said things should be cured after around 200 hours or so of operation. Right this moment I'm doing a couple of huge downloads, have 3 different windows open and running ConvertAll to get my numbers correct, (Sorry, I hate metric), and it's holding steady at just under 30C (85F). Compared to the P4 specs, this is just fine!

Here are some more specs for this system. I'm running a Micro ATX Apevia box that has 4 fans total. One 120mm in the PS, one mobo speed controlled 80mm on the heatsink, one 80mm in the front of the case, and one Thermaltake 120mm adjustable speed fan on the back of the case that's only running at around 800 rpms. If it starts to run over the 38C (100F) mark, I can always turn up the speed on the main system fan, and it **will** cool it down! The case also came with a display that connect to two thermal pickups to monitor the temps of the CPU and an HDD, and they are dead on with the mobo readouts. OK. I'm a geek. The box is open, too. Has been for the last, um, couple weeks. :-$

BTW - Since I have 3HDDs in the box, I thought about running either dual-boot or virtualization for what little I use **M**egabuck**S** Winders XP. (Vista Sucks! See BlimpTv's commercial on youtube!) When I got everything set up and started the install, it was the first time I saw the temperature monitor pop 38C (100F) and cap out at 40C (104F). Proof positive that Ubuntu Linux is physically ***COOLER*** than Winders! :guitar:

Remember, intruders always enter through Windows! :-({|=

PS - Love your A.E. Neuman avatar.

---

### Post by chandra on 2009-03-13
Thanks for all the responses.

I can now answer my own question and say that the configuration > Motherboard: Gigabyte GA-MA78GM-S2H with AMD 780G + SB700 Chipset, ATI Radeon HD3200 IGP, and Realtek ALC889A codec
CPU: AMD Athlon 64 X2 5200+ AM2 Dual Core
Memory: Corsair 4GB kit Twin2X PC8500 1066MHz
HDD: SATA
DVD/RW: SATA works without incident both with Ubuntu and Kubuntu Intrepid running KDE 4.2.

The jockey-kde program prompted me to install proprietary drivers from ATI if I wanted. The display resolution and sound are fine. All in all, no major problems with this hardware :D

---

### Post by super.rad on 2009-03-24
Brilliant, am planning nearly exactly the same build as you. Whats the performance like? Any lags? Compositing working fine?

---

### Post by chandra on 2009-03-25
> **super.rad said:**
> Brilliant, am planning nearly exactly the same build as you. Whats the performance like? Any lags? Compositing working fine?

I have not detected any performance lags.

There are flicker problems viewing videos both with GNOME and KDE, but that appears to have something to do with Xv versus X11 rather than the motherboard or hardware setup per se, but I might be wrong. Once you deselect Xv on GNOME and run vlc, you can view flicker-free videos, with compiz running.

Both Compiz and Kwin work fine. On my previous PC, I could not get a transparent KDE konsole under KDE 4. Now, I am running KDE 4.2 and can get a transparent konsole with Kwin. I have not activated the more cutting edge plasma-based graphics, but am happy with the graphics that I have so far.

HTH.

---

