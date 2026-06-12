---
title: "Installing ubuntu server on an old computer? help!"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by Arwen17evenstar on 2009-09-25
I am trying to set up a ubuntu server on an old gateway computer running windows 98. I have two 128 mb RAM cards and no matter how I install them they don't go past 64 mb RAM being recognized. When I remove one of them, it goes back to 32 mb RAM. 

My biggest problem is that I cannot get ubuntu server to boot at start up. Unfortunately, I have everything, but CD-R's with me. First, I burned the .iso onto a CD-RW and that didn't work. Then I burned it onto a DVD-R and it sounds like it was spinning a bit, but it still didn't boot. I have bios set up to where it only boots the CD-ROM drive and nothing else and it keeps telling me to insert a bootable media. I did test a CD-R music cd of mine on the computer before hand and it played fine. So I know the disc drive works with music CDs.

Do you think I can't boot ubuntu server because I need to use CD-R, or because I don't have enough ram, or do I need to burn the .iso onto the disc at a slower speed? etc. etc.? I need tips on how to get a bootable disc to work on an old computer.
Is it possible to run ubuntu server on 64 mb RAM, even though in actuality I have two 128 mb installed?
I really want to experience having my own server, but so far, I keep hitting one brick wall after another.

---

### Post by rreese6 on 2009-09-25
I would say that you have hit a brick wall.
you need to get the memory issue solved
try each stick separately to see the size.
if they come up as 32M then the sticks are most likely 32 meg and not 128M. of course make sure your BIOS is set up correctly for the memory.
you might want to check the a memory compatibility site to make sure that memory will work in your system.
I think Kingston and Crucial have a site for that.

next once your memory problem is solved and you have at least 128M, you need to go get a blank CD and burn that. most likely your cdrom drive doesn't read dvd and you can not boot off of cd-rw.
of course you could try to boot off of a USB stick if your bios allows it, but that is another story

good luck

---

### Post by Arwen17evenstar on 2009-09-25
> **rreese6 said:**
> I would say that you have hit a brick wall.
you need to get the memory issue solved
try each stick separately to see the size.
if they come up as 32M then the sticks are most likely 32 meg and not 128M. of course make sure your BIOS is set up correctly for the memory.
you might want to check the a memory compatibility site to make sure that memory will work in your system.

I know the sticks are 128mb and 166mhz because I just bought them off ebay to try to upgrade my ram. My gateway machine originally had just a 32mb ram card and its a 200mhz machine. As to whether the two 128m cards are compatible, I don't know, I was just guessing, but they did increase the ram to 64mb together and the computer is recognizing them just not the full 128mb. It makes me think each ram slot is only allowed 32mb each.

So is something in bios not set up right with regards to the new ram? I've been reading a lot about 'clock speeds' or something of that nature that confuses me, does that have anything to do with this? Or is my motherboard only able to hold a certain maximum of ram no matter what you stick in there?

---

### Post by rreese6 on 2009-09-25
Most likely the ram is not compatible with your system.
OK post the specs of your system, I will do some research.
also any data you have on the memory sticks.
get as much data as you can for me about the motherboard or at least unit model number.

---

### Post by Arwen17evenstar on 2009-09-26
On the back of the computer:
Gateway 2000, Inc.
P55C-200
Model No. LPMINI-Tower
Lot: 0007034272 
Serial No: 0007034272
MFG Date: 4/25/97
Input: 100-120/220-240 V. 50/60Hz Amp. 4A/2A

Harddrive: Maxtor model: 83200A5

Video card: which has so many numbers and stickers on it I don't know what the model number is
1X0-0491-303
18  15/2007
210-0262-00X
barcode label: 6000564
tiny little sticker: 4/25/07 07034272

AudioPCI:
tiny little sticker: 4/25/07 07034277
E237776 AudioPCI 9716
AssyNo: 01 Rev: E Assembled in USA
6000566

On to the motherboard: I think these are chipset thingys.
Intel PCIset
SB82437VX
L7040024
SU116
Intel '95

intel
SB82371SB
L7051489
SU093
Intel '95

SMC
FDC37C932FR
C9630-D5572
6M86027-7
American Megatrends 1994

Stickers on the motherboard itself:
AA 666761-205
barcode:4000253
barcode:W00193452

New RAM card: MT8LSDT1 664AG-133E1
PC133U-333-542-A
My M00UXRH 200131
128 MB 133mHz

Original RAM card:
sticker: Toshiba
THMY644021AEG-10
9716

printed on the card itself:
Toshiba G79723
9704MBD
Japan
TC5951608AFT-10

Let me know if there is some number I missed that you need; If you need more stuff about the harddrive or power supply etc. And there were a few more numbers on the motherboard, but there's so much going on there I can't tell what's what.

---

### Post by Arwen17evenstar on 2009-09-26
Here's my bios info if that helps:
American Megatrends, Inc. 1992
AMIBIOS 1.00.07.DQ0T

I found my motherboard!
[here!]("http://www.recycledgoods.com/18019_Gateway_4000253_Socket%207%20System%20Board%20-%20AA666761-205_.html")
SMBIOS Info
gateway bios
Manufacturer: Intel 
Product Name: MA430VX
Version: AA666761-205
Serial Number: W00193452

---

### Post by louieb on 2009-09-26
> **Arwen17evenstar said:**
> I know the sticks are 128mb and 166mhz ... It makes me think each ram slot is only allowed 32mb each.

Thats probably right. I still have motherboard that will only recognize 128MB per slot. Put a 256MB chip in one of the slots and only 128MB gets used.
Edit
On a whim googled your motherboard. lol- Found your post on the Tech support forum. Also found a memory store that says it maxes out at 128MB. - 2x64MB  PC66 SDRAM. [http://www.memoryx.net/intelaih.html](http://www.memoryx.net/intelaih.html)

---

### Post by Arwen17evenstar on 2009-09-26
From what I've gathered about my motherboard is that an sdram dimm combination cannot go higher than 64mb and an edo dimm cannot go higher than 128mb.

---

### Post by louieb on 2009-09-26
> **Arwen17evenstar said:**
>  an edo dimm cannot go higher than 128mb.

ut-oh time my age showed. IIRC edo memory is 72 pin. And will not fit in an SDRAM slot.

---

### Post by rreese6 on 2009-09-26
After spending the past 4 hours researching this. I see you have your answer already.
the unit can not recognize more than 64M for the SDRAM slots you have.
if you had 72 pin EDO then it would have been 128. Still that would have been a difficult if not impossible board to put ubuntu on.
The memory was specially made for that motherboard during a time when
motherboards were changing from EDO to SDRAM. The Chips had a different configuration than you have now. The memory speed was usually 66Mhz but there was a "high-end" 100mhz memory made by Seimens (and Toshiba).
those boards are no longer available any where (except maybe in my junk box). 
You might was to try DSL (Damn Small Linux) on it and see if it will run. another option might be an old version pf puppy Linux like versioin 2.15  or less.

Sorry for the bad news.....of course you could add another network card and turn it into a router using Smootwall ([www.smoothwall.org](www.smoothwall.org))
That is what I would probably use it for.

take care

---

