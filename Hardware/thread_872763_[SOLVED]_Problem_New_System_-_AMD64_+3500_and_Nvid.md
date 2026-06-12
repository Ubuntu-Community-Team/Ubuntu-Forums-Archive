---
title: "[SOLVED] Problem: New System - AMD64 +3500 and Nvidia GeForce 7300GS"
date: 2008-07-28
forum: Hardware
---

### Post by Bruce M. on 2008-07-28
Hi Folks,

I'm at a loss. I have a new system sitting on the table behind me.
[LIST]
[*]**Motherboard:** MSI K8N Neo4-F
[*]**CPU:** AMD Athlon 64 +3500
[*]**RAM:** 2G - (Set for duel channel 128bit)
[*]**HD:** 200GB - Maxtor
[*]**DVD:** Sony DVD RW
[*]**DVD:** LG Super Multi DVD Drive Model: GSA-H10L (not connected at the moment)
[*]**Video:** Nvidia GeForce 7300GS Graphics Card
[/LIST]
To be installed later:
[LIST]
[*]Creative Sound Blaster Audigy 4 Card c/w Remote Control and Sensor Unit.
[*]Kensington - Wireless, Optical 5 Button Mouse
[/LIST]
I'm anxious to get it up and running with Linux, see my sig and you'll know why, but that **Nvidia GeForce 7300GS** is causing problems.

**EDIT:** Not the Nvidia GeForce card at all... it is something else.

My Xubuntu 8.04 "Live CD" will not run on it. It stars I see a lot of errors fly by and then the start-up screen with the blue bar sliding back and forth, and there it stays.

I popped in the Xubuntu Alt CD, saw the errors flash by but the Meun came up, did the install and everything went well until it came time to take the CD out and hit enter to continue. The results were the same as the Live CD --- blue bar sliding back and forth.

I've read where "ENVY" is a way to load restricted drivers for the card but I can't get into the system to do that.

The MSI MOBO has NO built in VGA display so I need a video card and only have the one.  :(

Any ideas on how to get this working short of buying another card?

Have a nice day.
Bruce

**PS:** When I couldn't get it running I Installed W2K just to see if the system is put together correctly with everything working. W2K installed fine and the video card CD installed the drivers just fine.

**SO:** I know that the system works, just not with Ubuntu.

[CENTER]**Help, please!**[/CENTER]

---

### Post by mdpalow on 2008-07-29
bump. I'm curious too.

---

### Post by Bruce M. on 2008-07-29
Coming at you from an Ubuntu 8.04 (64bit) Live CD session - so no email yet, no anything for that matter.

I tried three more attempts and finally Xubuntu "was" on the new machine. I unplugged it to add a second HD and DVD player and all hell broke loose. Xubuntu would not start up, would not reinstall. In fact I'm on day 4 with this problem. The P-III finally died, I think it was the Lan Card (built in) as it wouldn't go on the net.

All day I've had problems with this new AMD64 machine. When trying to install I get errors right after I see "Loading Linux Kernel", the screen goes black and I see text fly by:

ata1.00 status {DRDY ERR} blah blah ...
ata1.00 status {ICRC ABRT} blah blah ...
ata1.00 exception Emask blah blah ...
ata1.00 BMDMA stat 0x64 blah blah ...

more stuff then it looks like it repeats for

ata1.01  (( sigh ))

At which point the boot process starts and completes right up to the loading "sliding bar" after removing the CD.

If I leave it alone long enough I finally get a black screen with:

BusyBox v1.1.3 .... built in shell (ash)
(initramfs) _

I am at a complete loss ... tried that all day until finally I said "BASTA!" (Enough) and installed W2K so I could at least get Firefox and Thunderbird, restore my bookmarks and email and have something to work with.

Wouldn't you know it, I have the "safest installed Windows" in the world! - I have no modem and W2K can't find the LAN card on this motherboard.

Pop in this Live CD and here I am.

I think this computer is the computer from "Hell", W2K loads but won't get out to the net, Ubuntu won't load but the Live CD goes on the net just fine. And my P-III is dead.

Talk about a rock and a hard place.  :(  Time for a break ... 

Any help out there at all?
Have a nice day.
Bruce

---

### Post by Bruce M. on 2008-07-30
Hi Folks...

OK, some added info I just noticed.

LIVE CD Session ... the only way to get Ubuntu to work.

My start up screen...

```
Phoenix Award BIOS v6.00PG, An Energy Star Ally
Copyright (c) 1984-2005, Phoenix Techix Technologies, LTD.

W7185NMS v1.8 082406 13:33:03

Main Processor: AMD Athlon (tm) 64 Processor 3500+
Testing Memory: 2097152 OK
Frequency: 201MHz Tcl:3  Trcd:3  Tras:8  Trp:3 (2T Timing)

PCIE VGA Link Width: x8

IDE Primary Master: Maxtor 6L200PO BAJ41G20
IDE Primary Slave: WDC WD800 BB-55JKC
IDE Secondary Master: Sony DVD RW AW-Q170A 1.70
IDE Secondary Slave: HL-DT-ST DVDRAM G

IDE Primary Channel  no 80 conductor cable installed
IDE Secondary Channel  no 80 conductor cable installed
```

OK, if I have no IDE Primary or Secondary cable installed how the heck can it see my DVDs and HDs?

Is this causing the error I see at post #1?

**Please Help**

Thanks.
Bruce

---

### Post by kaivalagi on 2008-07-30
> **Bruce M. said:**
> Hi Folks...

OK, some added info I just noticed.

LIVE CD Session ... the only way to get Ubuntu to work.

My start up screen...

```
Phoenix Award BIOS v6.00PG, An Energy Star Ally
Copyright (c) 1984-2005, Phoenix Techix Technologies, LTD.

W7185NMS v1.8 082406 13:33:03

Main Processor: AMD Athlon (tm) 64 Processor 3500+
Testing Memory: 2097152 OK
Frequency: 201MHz Tcl:3  Trcd:3  Tras:8  Trp:3 (2T Timing)

PCIE VGA Link Width: x8

IDE Primary Master: Maxtor 6L200PO BAJ41G20
IDE Primary Slave: WDC WD800 BB-55JKC
IDE Secondary Master: Sony DVD RW AW-Q170A 1.70
IDE Secondary Slave: HL-DT-ST DVDRAM G

IDE Primary Channel  no 80 conductor cable installed
IDE Secondary Channel  no 80 conductor cable installed
```

OK, if I have no IDE Primary or Secondary cable installed how the heck can it see my DVDs and HDs?

Is this causing the error I see at post #1?

**Please Help**

Thanks.
Bruce

Doing a search thru google for "no 80 conductor cable installed" I find this:

[I]"It means you're still using the 40 conductor cable from the MB IDE to the hard drive. The 80 Conductor Cables are used to take advantage of the newer Ultra/ATA-66 and up IDE drives. (They will still work with the 40
conductor cable, just slower.)"[/I]

and this:

[I]"With some chipsets DMA will have some troubles with 40-pin IDE cables, when they're attached to 2 hard drives. (From experience, this happens more when both are set to Cable Select or CS).

My advice is get a propper ATA133 80-pin IDE cable, or another one if it still complains about it if you have one, the bottom line is that the Parallel Input/Output principals are extremely inefficient and outdated can bottleneck even a 5400rpm IDE drive. So make sure you can get DMA active like Mix-Master says if at all possible for a speed and stablility increase."[/I]

I suggest getting hold of a 80 pin connector cable, and then see what happens...

You can get it working with one drive right? The second of the suggestions above mentions it being more of a problem when two drives are connected...

---

### Post by Bruce M. on 2008-07-30
> **kaivalagi said:**
> Doing a search thru google for "no 80 conductor cable installed" I find this:

[I]"It means you're still using the 40 conductor cable from the MB IDE to the hard drive. The 80 Conductor Cables are used to take advantage of the newer Ultra/ATA-66 and up IDE drives. (They will still work with the 40
conductor cable, just slower.)"[/I]

and this:

[I]"With some chipsets DMA will have some troubles with 40-pin IDE cables, when they're attached to 2 hard drives. (From experience, this happens more when both are set to Cable Select or CS).

My advice is get a propper ATA133 80-pin IDE cable, or another one if it still complains about it if you have one, the bottom line is that the Parallel Input/Output principals are extremely inefficient and outdated can bottleneck even a 5400rpm IDE drive. So make sure you can get DMA active like Mix-Master says if at all possible for a speed and stablility increase."[/I]

I suggest getting hold of a 80 pin connector cable, and then see what happens...

You can get it working with one drive right? The second of the suggestions above mentions it being more of a problem when two drives are connected...

What? Oh my, but the board and back of the drives only have 40 pins?

How does this work?

CHIMO!
Bruce

EDIT> Never mind ...

> (it's got two fine wires per connection)

Off to the store ... I will be back.
CHIMO!

---

### Post by mdpalow on 2008-07-30
> **Bruce M. said:**
> Hi Folks...

OK, some added info I just noticed.

LIVE CD Session ... the only way to get Ubuntu to work.

My start up screen...

```
Phoenix Award BIOS v6.00PG, An Energy Star Ally
Copyright (c) 1984-2005, Phoenix Techix Technologies, LTD.

W7185NMS v1.8 082406 13:33:03

Main Processor: AMD Athlon (tm) 64 Processor 3500+
Testing Memory: 2097152 OK
Frequency: 201MHz Tcl:3  Trcd:3  Tras:8  Trp:3 (2T Timing)

PCIE VGA Link Width: x8

IDE Primary Master: Maxtor 6L200PO BAJ41G20
IDE Primary Slave: WDC WD800 BB-55JKC
IDE Secondary Master: Sony DVD RW AW-Q170A 1.70
IDE Secondary Slave: HL-DT-ST DVDRAM G

IDE Primary Channel  no 80 conductor cable installed
IDE Secondary Channel  no 80 conductor cable installed
```

OK, if I have no IDE Primary or Secondary cable installed how the heck can it see my DVDs and HDs?

Is this causing the error I see at post #1?

**Please Help**

Thanks.
Bruce


Maybe you have a bad cable. One that is partially working and causing you problems???

good luck

---

### Post by Bruce M. on 2008-07-30
[B][CENTER]Coming at you LIVE from the WRSSC Computer
It's show and tell time!!![/CENTER][/B]

> **mdpalow said:**
> Maybe you have a bad cable. One that is partially working and causing you problems???

good luck

Cables were good, but only 40 pin. I'm really new to these new **super** home computers and had no idea they existed.

> **kaivalagi said:**
> Doing a search thru google for "no 80 conductor cable installed" I find this:

[I]"It means you're still using the 40 conductor cable from the MB IDE to the hard drive. The 80 Conductor Cables are used to take advantage of the newer Ultra/ATA-66 and up IDE drives. (They will still work with the 40
conductor cable, just slower.)"[/I]

and this:

[I]"With some chipsets DMA will have some troubles with 40-pin IDE cables, when they're attached to 2 hard drives. (From experience, this happens more when both are set to Cable Select or CS).

My advice is get a propper ATA133 80-pin IDE cable, or another one if it still complains about it if you have one, the bottom line is that the Parallel Input/Output principals are extremely inefficient and outdated can bottleneck even a 5400rpm IDE drive. So make sure you can get DMA active like Mix-Master says if at all possible for a speed and stablility increase."[/I]

I suggest getting hold of a 80 pin connector cable, and then see what happens...

You can get it working with one drive right? The second of the suggestions above mentions it being more of a problem when two drives are connected...

DA... er... Darn, I love it when you're right!
Went to the store and came home with two 80pin cables just to be safe. The two DVD players are on them as well.

Man oh man, the speed... and multitasking in real time not slow motion :)

[COLOR="Blue"][SIZE="7"][CENTER]**I LOVE IT!!**[/CENTER][/SIZE][/COLOR]

Ooops, gotta change my sig!  :)

CHIMO Guys and a million thanks for your support!!!!!
Bruce

---

### Post by kaivalagi on 2008-07-31
> **Bruce M. said:**
> [B][CENTER]Coming at you LIVE from the WRSSC Computer
It's show and tell time!!![/CENTER][/B]



Cables were good, but only 40 pin. I'm really new to these new **super** home computers and had no idea they existed.



DA... er... Darn, I love it when you're right!
Went to the store and came home with two 80pin cables just to be safe. The two DVD players are on them as well.

Man oh man, the speed... and multitasking in real time not slow motion :)

[COLOR="Blue"][SIZE="7"][CENTER]**I LOVE IT!!**[/CENTER][/SIZE][/COLOR]

Ooops, gotta change my sig!  :)

CHIMO Guys and a million thanks for your support!!!!!
Bruce

That's great, you're now free from the old hardware shackles :)

---

