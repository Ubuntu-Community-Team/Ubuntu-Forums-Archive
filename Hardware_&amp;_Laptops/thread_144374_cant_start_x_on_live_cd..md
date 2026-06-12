---
title: "cant start x on live cd."
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by kurrupted on 2006-03-14
Hi guys,

I just got my ubuntu cd's in the post this morning and tried to run the live cd.

when i just let it run after detecting everything the screen just kept slowly fading from black to white and vice verca.

so i tried to look at the help and tried booting with,

boot: live vga=771 noapic nolapic

and eventually after going through all the options it informed me that x couldnt be started. :confused: 

my system is as follows;

CPU	Intel Pentium 4 540 w/HT (3.2GHz)
LCD	17" WXGA+ BrightView WideView (1440x900 max)
RAM	512MB
HD	60 GB
CD/DVD	DVD/CD-RW Combo Drive
VIDEO	128MB ATI Mobility Radeon X600
SOUND	Intel AC97 based integrated sound
Modem/Network	Integrated 56K Modem+10/100 Ethernet LAN
Battery	12 Cell Lithuim Ion Battery

any ideas... ?

Please!

Jay

---

### Post by mavr on 2006-03-14
I am not an expert on Live nor on graphic card, but i think your problem could be on the driver that get's loaded. Check xorg.conf if there is one somewhere on a live, and see what driver it's loading. I am not sure, you'd better check it (try to put your graphic card in search field on this forum), but i think your card should be using ati driver.

---

### Post by Okami on 2006-03-14
I dont think this will help but maybe... open your Xorg.conf file from the command line and add an # before Load "dri" in section module. This (if it helps) will only give 2d... also I think the driver in section device should be radeon.
This is what I had to do to be able to start x, but I dont have the same card.

Sorry for my bad english.

---

### Post by spandon on 2006-03-15
Hi Kurrupted,
try:
Live apci=off, hw-detect/start_pcmcia=false, vga=771
This works with my Acer 1652 with an ATI x300 in breezy 5.10 both in ubuntu and kubuntu.
But nothing seems to work for dapper f4 and f5,hopefully this gets fixed for final release.
Don

---

### Post by kurrupted on 2006-03-16
I have had a good search on the net and found it can be done... i have ben meaning to re-install windoze ever since my brother in law screwed the system up and i had to hack into the admin account to regain control of the machine.

( i just need to find the cd now!!! )

what i'll do is do a dual boot system:

i have an 80gb hdd

what i want to do is have 30 gb for doze 30 for ubuntu and a 20 gig area for my mp3's and avi's accessable by both OS's...

what format do i need to format each of the sections into i know thw doze section will need to be ntfs but what about the ubuntu section and the one for the mp3's?

thanks!

Jay

---

