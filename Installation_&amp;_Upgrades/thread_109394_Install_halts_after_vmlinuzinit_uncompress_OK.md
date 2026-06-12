---
title: "Install halts after vmlinuz/init uncompress OK"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by deangl on 2005-12-28
Hi,

I am trying to boot the 5.10 live CD (also tried install CD with same results) on a Compaq Presario SV1010 desktop system.  

The install process (GRUB?) asks for boot sequence/parameters.  I have tried CR and also tried multiple combinations of params listed in the F5F6F7 help screens - to no avail.  After I see the uncompressing vmlinuz and init messages zoom by, the screen is cleared and the next thing I see is the system restarting (BIOS startup messages).   :( :( :(     This system is a little more than a year old.

I searched some on the docs and wiki - but those seem to be poor resources (no hits - either I am searching for the wrong terms or in the wrong way...)

I seem to be really stuck.  Any pointers would be extremely appreciated.

Thanks,
Dale

---

### Post by deangl on 2005-12-28
Additional info: main board is MS-6577 (Giovani) M-ATX Rev 3.1 (according to HP/Compaq website).  It has Celeron 2.58 CPU, also Intel 845GV chipset.  

I saw a post on another site where the author changed BIOS param for HDD Access mode from AUTO to LBA (and also noapic).  I also tried these, but no success yet.

All help is appreciated - I am currently stuck.:( 

Thanks,
Dale

---

### Post by deangl on 2005-12-28
Success!!!

I found that just using "linux acpi=off" was sufficient.

My configuration is Compaq SR1010V
Mainboard - MS6577 (Giovani)
CPU - Celeron D at 2.58GHz
Video - Intel 845GV
Intel ICH4
Memory - 512Mb
Disk - 40Gb

Hopefully this will be helpful for others.  I saw a lot of threads across different Q&A forums regarding this and similar problems ranging from mid 2004 to just a few months ago.  None of the ones I saw discussed this specific syntax above.

There is joy in mudville...

Dale   :-)

---

### Post by shmatt on 2007-07-10
How do I turn "'linux acpi=off"? I looked thru the bios and I'm not finding anything to do with acpi. 

I'm using a  MS 6577 ver 4.1 mainboard and the instant reboot is driving me nuts.

Thanks in advance to anyone that can help!

---

### Post by gss6 on 2007-07-13
When the system boots from the LiveCD Before making a selection press F6 and type "linux acpi=off".

---

### Post by shmatt on 2007-07-15
Thanks for the response! I did that and everything was go until it came to loading hardware drivers. It  basically crashes at "[107.817178] agpgart: AGP aperture is 128M @ 0xd00000".

Is this MS-6577 motherboard a lost cause?

---

### Post by shmatt on 2007-07-16
I tried installing with the live cd a few more times with linux acpi=off and strangely now it gives me this message:

[103.198472] <0> Kernel Panic - not syncing: Fatal exeption in interrupt.

---

### Post by Pumalite on 2007-07-16
Why don't you try the 'Alternate CD'?

---

### Post by shmatt on 2007-07-17
I tried the gutsy alternate cd and I got "system halted: crc error".

---

### Post by Pumalite on 2007-07-17
Not a good idea to start with Gutsy when you are a newbie. I would stick to Feisty for now. Beyond that, you may have other problems: bad iso, corrupted CD, graphical interface problem, low memory, etc. Why don't you tell us a little bit more? Hardware wise.

---

### Post by dbillings on 2007-07-23
I have the exact same problem and error message. I used MD5 to check the ISO and the hashes matched. I also successfully ran the CD on a seperate system. The ISO I'm trying to use is Ubuntu 6.06.1 - desktop-i386. Any help would be appreciated 

I have a 
Compaq Presario SR1218NX
330 Intel Celeron D 330 Processor
256 MB PC 2700 DDR SD RAM
Intel MS-6557 Motherboard

---

### Post by Pumalite on 2007-07-23
256 MB RAM or less> Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by dbillings on 2007-07-24
Thank you. I'll give it a shot.

---

### Post by dbillings on 2007-07-24
No good install locks up. Here's a screenshot of the lockup.

[IMG]http://i2.photobucket.com/albums/y46/dennisbillings/ubuntuhelp.gif[/IMG]

---

### Post by Pumalite on 2007-07-24
You probably have integrated video. Do you?

---

### Post by dbillings on 2007-07-24
Yes, I do. Integrated 3D/2D graphic core 

Here it is [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=130136706590&ssPageName=MERCOSI_VI_ROSI_PR4_PCN_BIX&refitem=270145635935&itemcount=4&refwidgetloc=closed_view_item&refwidgettype=osi_widget](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=130136706590&ssPageName=MERCOSI_VI_ROSI_PR4_PCN_BIX&refitem=270145635935&itemcount=4&refwidgetloc=closed_view_item&refwidgettype=osi_widget)

---

### Post by Pumalite on 2007-07-24
You might have to go with zenwalk or DamnSmallLinux

---

