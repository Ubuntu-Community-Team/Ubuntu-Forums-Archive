---
title: "please help me install an ide pci card"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by benner on 2007-05-04
i have a 64 bit system running ubuntu feisty.  i am trying to install a Link-Max WD-8212 32 bit ATA/133 IDE (RAID) Card (PCI Bus 2.1 and 2.1)

the disk has a folder with a couple of drivers called iteraid.o and iteraid.smp

i have no idea what to do with them.  i have the card installed.  i have a cd-rom connected to the card.  i looked in the dev folder and it didn't look like it was there.  i see:

IT/ITE8212 Dual channel ATA RAID

listed in the device manager and PCI.product lists it as an 8212 so it appears that ubuntu knows it is there.  what next?

---

### Post by ohgod on 2007-05-04
I haven't used raid cards from that manufacturer before, but with the raid cards I have used you have to reboot and hit a key during the raid card's bios load (you should see that on the screen).  Once you get into the card's bios screen you can create the array.  Then hopefully ubuntu will see it when you boot up again.  The manufacturer's website will probably have more info.

---

### Post by benner on 2007-05-04
i've never noticed it at boot time before but i will give it a shot...  thanks.

do those driver files names mean anything to you?

---

### Post by dannyboy79 on 2007-05-04
> **benner said:**
> i have a 64 bit system running ubuntu feisty.  i am trying to install a Link-Max WD-8212 32 bit ATA/133 IDE (RAID) Card (PCI Bus 2.1 and 2.1)

the disk has a folder with a couple of drivers called iteraid.o and iteraid.smp

i have no idea what to do with them.  i have the card installed.  i have a cd-rom connected to the card.  i looked in the dev folder and it didn't look like it was there.  i see:

IT/ITE8212 Dual channel ATA RAID

listed in the device manager and PCI.product lists it as an 8212 so it appears that ubuntu knows it is there.  what next?

if it's just for a cd-rom, then just add an entry to your fstab like this
(note: you can have it be moutned to whereever you want, just make sure you create the folder you want cd's and dvd's mounted to. per below I have a folder within /media called cdrom0 which all my dvd's and cd's get automatically mounted to when I insert them)

/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

BUT you'll need to change the /dev/hda to be whatever your cdrom is showing up as. this can normally be found out by looking thru the dmesg file. just type this into a terminal

dmesg | grep CD

OR

dmesg | grep DVD

here is what mine returns:

dmesg | grep DVD
[17179576.740000] hda: Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive
[17179577.908000]  hdb: hdb1 hdb2 <<6>hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)

OR

dmesg | grep CD
[17179576.740000] hda: Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive
[17179577.908000]  hdb: hdb1 hdb2 <<6>hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179577.912000] Uniform CD-ROM driver Revision: 3.20

These both tell me that the cdrom/dvdrom is device hda.

good luck

---

### Post by dannyboy79 on 2007-05-04
> **ohgod said:**
> I haven't used raid cards from that manufacturer before, but with the raid cards I have used you have to reboot and hit a key during the raid card's bios load (you should see that on the screen).  Once you get into the card's bios screen you can create the array.  Then hopefully ubuntu will see it when you boot up again.  The manufacturer's website will probably have more info.


it doesn't say he want to create a raid array, he stated that he has a cdrom hooked to it.

---

### Post by dannyboy79 on 2007-05-04
> **benner said:**
> i've never noticed it at boot time before but i will give it a shot...  thanks.

do those driver files names mean anything to you?

I wouldnt' ever use a pci raid card for raid unless you spent over a couple hundred dollars on it as it's NOT true raid. just use software raid in linux, it's better than the fake raid that cheap raid cards propose. Also, do you even have any hard drives hooked up to your pci raid card? you stated you only a cdrom.

---

### Post by benner on 2007-05-05
thanks for the replies.  actually, i'm not entirely sure what RAID is.  the motherboard only has one ide socket.  everything else is what i assume to be SATA (much smaller sockets, thin cable.  so i have a 250gig hard disk attached to a SATA socket.  then i have an ide cable the connects to a dvd burner and a second hard drive that is 80gigs.  the guys who sold me tho computer game me this pci card that has 2 additional ide sockets.  i haven't been able to get it to work.  but now i have another cd-rom that i want to attach so i used another ide cable and attached it to the card.  the rest in in the first post.  i can see the card in the device manager.  i don't see the cd-rom.  in the /dev folder i don't see it either.  i could be missing something though.  it is a bit confusing.  i think the dvd burner comes up as more than one device, right?  bummer that this is not easier but i am willing to try to learn and sort this out if anyone is prepared to bear with me and try to help.  i appreciate your efforts.

---

### Post by dannyboy79 on 2007-05-07
you simply need to make sure that you're loading the correct module for the pci card. you say that you see the card in the device manager. what does it all say? Also, I am not trying to be rude but it's really frustrating trying to help someone when I specifically asked you for some info and you posted back but didn't include any of the info that I asked for. How can anyone help you if you don't help us help you. please post back what this returns as well as ALL the info that I have already asked for otherwise I can't help you. it's also more frustrating to people who are trying to help when they have to ask more than once for the info they need in order to provide you with help. it's pretty straight forward, you want help, we don't know your exact situation, the only way we can help is if we know more about your setup so we ask you to provide info.

lspci -v

---

### Post by benner on 2007-05-07
i'm sorry, what did I miss?  I tried 

ben@ramen:~$ dmesg | grep CD
[   39.176821] hda: LITE-ON DVDRW LH-18A1P, ATAPI CD/DVD-ROM drive
[   42.885430] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   42.885439] Uniform CD-ROM driver Revision: 3.20
 
which didn't show the cd-rom that I connected to the pci card.  it only showed the dvd-rw that is connected directly to the motherboard using the one ide port that was there.

so, there is a 250gig that is connected to SATA

there is an 80gig and a dvd-rw that are connected to the ide on the motherboard

there is a cd-rom connected to the pci ide card.  it does not appear anywhere.

the card appears in the device manager as:

Vendor: Integrated Technology Express, Inc.
Device: IT/ITE8212 Dual Channel ATA RAID
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

under the 'advanced' tab there is a ton of information.  i don't know what is useful there and I can't copy and paste it so i have to type it all in myself.

i tried to get into the card's bios at boot time and couldn't get very far.  i got into something about RAID setup and it looked like there was something about the card there that I selected 'enable' but there were no other options that i could select or change.  there was more stuff in there about RAID setup (IDE, Striped and some other choices that I didn't understand) so i din't change anything.  it looked like it was a setup for the motherboard, not the card.  

without seeing anything about it in /dev i guess there is nothing to do in fstab.

is there something else you wanted me to post that would help you?  i sincerely appreciate your helping me on this.  so often, people don't return to the thread to follow up.  thank you for doing so.

do those driver files mean anything to you?

---

### Post by dannyboy79 on 2007-05-07
> **benner said:**
> i'm sorry, what did I miss?  I tried 

ben@ramen:~$ dmesg | grep CD
[   39.176821] hda: LITE-ON DVDRW LH-18A1P, ATAPI CD/DVD-ROM drive
[   42.885430] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   42.885439] Uniform CD-ROM driver Revision: 3.20
 
which didn't show the cd-rom that I connected to the pci card.  it only showed the dvd-rw that is connected directly to the motherboard using the one ide port that was there.

so, there is a 250gig that is connected to SATA

there is an 80gig and a dvd-rw that are connected to the ide on the motherboard

there is a cd-rom connected to the pci ide card.  it does not appear anywhere.

the card appears in the device manager as:

Vendor: Integrated Technology Express, Inc.
Device: IT/ITE8212 Dual Channel ATA RAID
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

under the 'advanced' tab there is a ton of information.  i don't know what is useful there and I can't copy and paste it so i have to type it all in myself.

i tried to get into the card's bios at boot time and couldn't get very far.  i got into something about RAID setup and it looked like there was something about the card there that I selected 'enable' but there were no other options that i could select or change.  there was more stuff in there about RAID setup (IDE, Striped and some other choices that I didn't understand) so i din't change anything.  it looked like it was a setup for the motherboard, not the card.  

without seeing anything about it in /dev i guess there is nothing to do in fstab.

is there something else you wanted me to post that would help you?  i sincerely appreciate your helping me on this.  so often, people don't return to the thread to follow up.  thank you for doing so.

do those driver files mean anything to you?

ok, try this first before following the instructions below

modprobe it821x

this should enable this module. then see if you can see your cdrom? you could also view the dmesg output.

dmesg | tail

does it say anything about the modprobe command or the cdrom?


if that doesn't work you may need to enable it to be used as a module within the kernel. Here is the link to a guide that states it DOES work in dapper but you'll need to enable it in the kernel config. (this is why I think a modprobe should enable it as a kernel module just like one does for wireless etc etc)  within this link, what he is doing is applying a patch so that it works for the old kernel 2.6.12 but he did state in there that 2.6.15 the support built in but I don't think its a module? so to be honest you may need to ask some1 with more experience compiling kernels and how this all works.

[http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12](http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12)

BELOW is the link to compile the most recent kernel and all you should have to do is look thru the config and find where it states:

CONFIG_BLK_DEV_IT821X=???

and make sure it says

CONFIG_BLK_DEV_IT821X=m

here is the guide to compile the recent kernel:

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

I don't think you would have to apply the patch because the guy stated that it was fixed in dapper but that would lead me to believe that your card should be working? but it's possible that it's as easy as modprobing it?

the good news is that it's very easy to follow guide. don't be intimidated and follow the instructions very precisely. if you have a question please post it at the kernel compilation page as I have never compiled my own. or maybe even send a PM to the guy who wrote the guide about compiling the it821x for kernel 2.6.12 and I am sure he'd be able to help ya.

---

### Post by benner on 2007-05-09
i will read through the posts about recompiling the kernel.  in the meantime, here's what happened when i tried the first 2 pointers.  there are a couple things in there that don't look good.  i don't know what it means though.

here's what happened:

ben@ramen:~$ modprobe it821x
FATAL: Module it821x not found.
ben@ramen:~$ sudo modprobe it821x
Password:
FATAL: Module it821x not found.
ben@ramen:~$ dmesg | tail
[  207.360772] Losing some ticks... checking if CPU frequency changed.
[  420.881051] ISO 9660 Extensions: Microsoft Joliet Level 3
[  420.886541] ISOFS: changing to secondary root
[ 7098.451078] warning: many lost ticks.
[ 7098.451080] Your time source seems to be instable or some driver is hogging interupts
[ 7098.451089] rip __do_softirq+0x54/0xd0
[30397.987029] beryl[5395]: segfault at 00002b2fb59ea9b0 rip 00002b2fb59ea9b0 rsp 00007fff0cb3b3d8 error 14
[50895.157023] ISO 9660 Extensions: Microsoft Joliet Level 3
[50895.157430] ISOFS: changing to secondary root
[51367.587349] beryl[27090]: segfault at 00002b95fcaff9b0 rip 00002b95fcaff9b0 rsp 00007fffc58246a8 error 14


then i turned off beryl and...


ben@ramen:~$ dmesg | tail
[  207.360772] Losing some ticks... checking if CPU frequency changed.
[  420.881051] ISO 9660 Extensions: Microsoft Joliet Level 3
[  420.886541] ISOFS: changing to secondary root
[ 7098.451078] warning: many lost ticks.
[ 7098.451080] Your time source seems to be instable or some driver is hogging interupts
[ 7098.451089] rip __do_softirq+0x54/0xd0
[30397.987029] beryl[5395]: segfault at 00002b2fb59ea9b0 rip 00002b2fb59ea9b0 rsp 00007fff0cb3b3d8 error 14
[50895.157023] ISO 9660 Extensions: Microsoft Joliet Level 3
[50895.157430] ISOFS: changing to secondary root
[51367.587349] beryl[27090]: segfault at 00002b95fcaff9b0 rip 00002b95fcaff9b0 rsp 00007fffc58246a8 error 14


now because of some other issues involving random freezes (a lot of people have that it seems) and it sometimes hangs at boot time, and when i run the live cd i get the top resolution out of my monitor from the open source driver but when it is installed i get a weird greenish screen and have to lower the resolution one step, and beryl and compiz sometimes give me artifacts on the screen, i thought maybe to install a 32-bit feisty and see if there is any improvement.  is there anything wrong or stupid with installing the 32 on a 64 dual core?  

thanks for the advice so far.

---

### Post by dannyboy79 on 2007-05-09
> **benner said:**
> i will read through the posts about recompiling the kernel.  in the meantime, here's what happened when i tried the first 2 pointers.  there are a couple things in there that don't look good.  i don't know what it means though.

here's what happened:

ben@ramen:~$ modprobe it821x
FATAL: Module it821x not found.
ben@ramen:~$ sudo modprobe it821x
Password:
FATAL: Module it821x not found.
ben@ramen:~$ dmesg | tail
[  207.360772] Losing some ticks... checking if CPU frequency changed.
[  420.881051] ISO 9660 Extensions: Microsoft Joliet Level 3
[  420.886541] ISOFS: changing to secondary root
[ 7098.451078] warning: many lost ticks.
[ 7098.451080] Your time source seems to be instable or some driver is hogging interupts
[ 7098.451089] rip __do_softirq+0x54/0xd0
[30397.987029] beryl[5395]: segfault at 00002b2fb59ea9b0 rip 00002b2fb59ea9b0 rsp 00007fff0cb3b3d8 error 14
[50895.157023] ISO 9660 Extensions: Microsoft Joliet Level 3
[50895.157430] ISOFS: changing to secondary root
[51367.587349] beryl[27090]: segfault at 00002b95fcaff9b0 rip 00002b95fcaff9b0 rsp 00007fffc58246a8 error 14


then i turned off beryl and...


ben@ramen:~$ dmesg | tail
[  207.360772] Losing some ticks... checking if CPU frequency changed.
[  420.881051] ISO 9660 Extensions: Microsoft Joliet Level 3
[  420.886541] ISOFS: changing to secondary root
[ 7098.451078] warning: many lost ticks.
[ 7098.451080] Your time source seems to be instable or some driver is hogging interupts
[ 7098.451089] rip __do_softirq+0x54/0xd0
[30397.987029] beryl[5395]: segfault at 00002b2fb59ea9b0 rip 00002b2fb59ea9b0 rsp 00007fff0cb3b3d8 error 14
[50895.157023] ISO 9660 Extensions: Microsoft Joliet Level 3
[50895.157430] ISOFS: changing to secondary root
[51367.587349] beryl[27090]: segfault at 00002b95fcaff9b0 rip 00002b95fcaff9b0 rsp 00007fffc58246a8 error 14


now because of some other issues involving random freezes (a lot of people have that it seems) and it sometimes hangs at boot time, and when i run the live cd i get the top resolution out of my monitor from the open source driver but when it is installed i get a weird greenish screen and have to lower the resolution one step, and beryl and compiz sometimes give me artifacts on the screen, i thought maybe to install a 32-bit feisty and see if there is any improvement.  is there anything wrong or stupid with installing the 32 on a 64 dual core?  

thanks for the advice so far.

huh, i am not sure what to tell ya about the beryl segfaults. I know they aren't good. also the thing about the ticks, if it's cpu related as it says, this may not be good either? As far as the it821x, check out this thread, it should provide you some insight.

[http://ubuntuforums.org/showthread.php?t=431781&highlight=it821x](http://ubuntuforums.org/showthread.php?t=431781&highlight=it821x)

so it appears as though you still need to recompile the kernel to include the older it821x module. you may want to ask in that kernel compiling thread how exactly to do this as I haven't ever compiled a new kernel.

---

### Post by benner on 2007-05-09
thanks for your time.  i will dig in there and see what i can come up with.  maybe just running the 32-bit as a dual boot to see if it is any different first.  cheers.

---

### Post by dannyboy79 on 2007-05-09
i would doubt that they would only change the it821x in the 64bit and not the 32bit but as we very well know, installing ubuntu is simple as tieing your shoe, so it couldn't hurt to try.

---

### Post by save2 on 2007-11-04
I have similarf RAID card with ITE 8212 chipset. Ubuntu dapper (6.06) automatically discovers it.
I can also browser any HD I connect to it (maximum 4 drives).
However there are three issues with this PCI-IDE card:
1. you must define it to use your drives (at boot I hit Ctrl+E to enter the card bios setup).
2. it won't take CD-ROMs
3. can't boot XP if the boot device connected to that card (not sure why) amd didn't tested it with ubuntu boot yet.

then ubuntu see it as /dev/hdc and /dev/hdd .

---

