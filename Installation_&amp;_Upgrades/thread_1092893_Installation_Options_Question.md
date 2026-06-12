---
title: "Installation Options Question??"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by decaren on 2009-03-10
Okay I'm not sure of exactly how to go about this, so I'll give a little history.  I started using linux again about a year ago.  Today I have 6 computers and 5 run Linux.  Here is my current setup:

1. Acer Laptop - Ubuntu Studio 8.10 - General Purpose / Mobile Audio
2. Dell Desktop - Ubuntu 8.04LTS Server - Server
3. Home Built - Ubuntu Studio 8.10 - Audio Production Machine for Home Studio
4. Home Built (rack case) - Ubuntu Studio 8.10 - Mobile Audio(ONLY) Recording/Production Machine. 
5. Home Built (htpc case) - Mythbuntu 8.10 - HTPC MythTV PVR
6. Shuttle X27D - WinXP (Soon to be Ubuntu 9.04) - Internet and Office PC

Captain obvious aside, I work in pro audio, mainly for TV but have been working a lot more lately with music again (thank god).  So my actual question is about the laptop.  I use it mainly for keeping me organized on the road, but it sees it's fair share audio recording/editing on the run and even some video editing while I'm on the road.  I want to know what would be the best way to set it up.  I run a lot of programs on the machine now and I've been noticing some lag as I get into the audio programs and more and more stuff is showing up in my ps -ax lists as I install.  So my (actual) question is what would be the best solution for setup on the machine:

1. Dual boot Ubuntu 8.10 32-bit for office style work and Ubuntu 8.10 studio 64-bit for audio/video editing on separate partitions

OR

2. Use one partition and make separate instances in grub for kernels (2.6.27....generic and 2.6.27....rt) and load different sessions in gnome (office and audio/video) as I login?

OR

3. I'm open to suggestions

I know which would be the easiest, but I want to know which would be the best.  I'm not 100% on how to go about doing option 2 but I can work my way through it.  I've gotten my mobile audio machine pretty well streamlined with no networking, bare minimum module load, bare minimum software install.  I would like to have that on my laptop as well with option to reboot and go into the office world of internet and email again when done recording.  Also I was thinking about making a separate partition and mounting /home there so I could blast away installation at free will as I'm testing the setup if (pronounced when) I mess stuff up. Is this a pretty stable setup for /home??  

Real quick hardware check on the laptop.  Acer Extensa 4620Z. Intel Dual Core 1.5Ghz, 2Gb Ram, 160Gb HDD, DVD Burner, Wireless, 10/100Lan, Bluetooth option installed, SD/XD/MMC/MS PRO Reader, Firewire onboard, and firewire PCMCIA Card (Texas Instruments Chipsets both), Focusrite Saffire firewire audio interface, ProDrive 1Tb firewire eHDD, WD 160Gb USB eHDD.  If I missed anything, just ask.

Sorry about being so long winded but I wanted to provide as much info as possible.  Thanks a lot for any help or opinions.  All are welcome!!!

---

### Post by ridetheteapot on 2009-03-10
You can use grub to boot different kernels on the same partition, but if you're gonna do 32bit and 64bit, go with option 1. You want the whole 64 bit OS to take advantage.
What might be a good idea is to share the boot partition but uses separate partitions for the OS installs, and then have another separate for /home that you can also share. That makes 4 partitons total not including a swap.

---

### Post by decaren on 2009-03-12
So would it just be better to have 64-bit all around.  The only reason I was considering 32-bit was for flash.  Although I haven't tried the 64-bit flash, just been using the non-free package and it seems to just stop working sometimes while I'm browsing.  64-bit 8.10 and 64-bit 8.10 Studio on the same partition, /home on another and of course swap on another.  I'm no expert, but I can figure my way through stripping the un-used modules in Studio for what I need.  The next question would be is there a way to get x to load a certain session based upon what kernel loads. i.e. Generic kernel loads gnome with office/internet stuff, Real-time kernel loads gnome with audio editing stuff.  Outside of selecting a session at gdm.

---

### Post by decaren on 2009-03-15
Anyone?? Bump

---

### Post by Roger E Critchlow Jr on 2009-04-24
Basically, if you have two boots which have different system configurations, then it's easiest to keep them as separate installs with each on its own root partition.

And if you have two seriously different desktop configurations that you want to run, make them different user logins.

It's annoying when you have to redo the same configuration on the other install or the other user, but it's even more annoying when something you do to make one system/user work ends up breaking the other system/user.  

-- rec --

---

