---
title: "Problems installing ubuntu on my laptop"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by Aces on 2006-02-03
Hello there!

I've been trying to install ubuntu on my laptop. I've got a Fujitsu Siemens amilo m 3438.

I'm far from a linux expert but i'm willing to get started on it

I started with the 5.10 version. This one gave me problems after the instalation ejects you cd and reboots. Here the whole deal freeze on starting hotplug subsystem.

So i looked around and couldn't really find a solution to that so i tried the 5.04 version i had laying around. This one went past the hotplug and started setting up everything... So i tought ah good! But then it happend... Kernel Null pointer exception at 0000002

I've got no idea what's wrong and google hasn't helped me a lot so i tought i maight ask you nice people here

thanks in advance!

---

### Post by slavik on 2006-02-03
I got the same hotplug issue ... :(

tried acpi=off and noapic nolapic ... nothing.

---

### Post by Kiran on 2006-02-03
This is not a reply but a similar question.  (Sorry if that's a no-no, I'm not familiar with forum protocols).

I tried a live CD of Ubuntu on my Toshiba 1800 Laptop.  It runs at 700 (?) MHz and has 120 MB of RAM.  The screen wallpaper image appeared but no icons.  I understand I may have to increase the memory.  I actually prefer KDE and wonder if kubuntu may work better.  I don't want to clear out my Windows applications unless I can reasonably expect ubuntu (kubuntu) to work.

Any suggestions?

---

### Post by Pkirkham on 2006-02-03
I heve the same issue on a recent ACER deskside machine hich only has SATA disks. I tried going back a version but that doesn't like the absence of IDE disks.
I get the impression that if I could edit the /etc/hotplug/blacklist to stop the hotplug initialisation trying to load the driver for a USB multicard reader which is on the motherboard and thus I can't physically remove, I might be ok. However since I don't know the name of the driver I'm wanting to blacklist nor how I can edit the file (I can't use my usual trick on using a Knoppix live CD since it won't boot on this SATA only system either).

So how do I find the awkward driver? Suggestions for either jumping the hotplug init completely or editing the file.

Hoping for a reply,
Pete

---

### Post by slavik on 2006-02-03
knoppix livedvd boots up fine (4.0.2) ...

---

### Post by UK31337 on 2006-02-04
I can get Knoppix to boot, but it locks up when you access the Internet for a few minutes.

I've also got the M3438G, same as the original poster.  I can't get the LiveCD to start (same hotplug issues), I've burnt the actual HD 5.10 to CD, but I doubt it'll run for me either.

Why isn't this obvious incompatibility being fixed?  It's some piece of hardware, nobody knows what is it, is it USB, ACPI, what?

That's the annoying thing, if I knew what didn't work it wouldn't bother me so much.

I had high hopes for Ubuntu, but I think I'll just go and grab SuSe instead.  Ubuntu will run through VMWare (I've tried it) but I want it to be properly installed and stand-alone.

---

### Post by Aces on 2006-02-25
A little bump...
Has anybody got an idea to solve this please?
I need linux for school urgently... Right now the 5.04 is turning with acpi=cpufreq i'm not sure if that could be a problem but i'd rather have a decent version running...
I do have this problem with my wireless too... It reconizes my card but i don't seem to get an ip adress from my router... 

Anyway i could really appreciate it if somebody could help me out. Eighter by helping me getting the 5.10 running or telling me what the cpufreq does exactly and if it could be dangerous to my laptop?

---

### Post by henac84 on 2006-02-25
Hello all!
I have a Philips Freevents laptop running XP. The Live CD or Install CD arent work on my machine. :( I get to the screen which says Uncompressing Linux... Ok Booting from the kernel and then it stops! Same problem with both CDs. I tried doing everything on page [https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)
which basically describes methods to boot Ubuntu without using any removeable media. Same problem remains! Please help!!

Specs follow:
Processor Type 	INTEL PENTIUM M 	
Processor speed 	1.73 	 	
Operating system 	XP HOME 	
Memory Type 	DDR 333 	
Hard Drive Capacity 	60 	
Memory Size 	1024 	
Graphics Card Type 	INTEL GMA900 	
Graphics Memory 	128mb shared 	
Sound Type 	AC97 16bit 	
Modem Type 	56k 	
Other Interfaces 	WIFI 802.11b/g

---

### Post by Aces on 2006-02-25
I've found a solution for the other people with the same problem.
With some others it works when you disable onboard audio...
I've looked all around in my bios and i can't find this option...

---

### Post by zolero on 2006-03-05
Hi there!

Recently I've purchased a new Asus A3H 5010 notebook PC, and I tried installing a dual-boot system on (with Win XP Pro SP2 and Ubuntu Breezy). All job was well done with install, but after the first reboot upon install the bootup process stops at following: starting hotplug subsystem...

Naturally, I've tried to start install with "noapic nolapic noacpi acpi=off" parameters but the result was same. How can I figuring out this? Had anyone a suggestion, a trick, or somewhat....?

Thx, Zolero.

Machine hardwares: Intel Celeron M380 Dothan FSB 533 MHz on 910 GMLE chipset, 768 Mb DDR2 533 MHz, 40 Gb HDD IDE Hitachi, 15" XGA TFT on video Intel 910 GMLE 128 Mb shared on board, audio Intel Realtek on board, 4xUSB 2.0, IEEE 1394, LPT, S-Dout, Realtek LAN, Connexant HSF Data/Fax Audio Modem, DVD-RW dual layer. No wireless, PCMCIA and cards.

---

