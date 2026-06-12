---
title: "Dell C521 Low Profile Computer + Ubuntu"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by kisain on 2007-05-31
ok i just got a shiney new Dell C521 with 4gb of ddr2 and a 500gb sata HD
it also has a low profile ati radeion x1300 pro low profile card.

here are the complete specs: 
dim c521,A64,X2,4600+ (2.8GHZ) 
19IN e197fpf,,dim,s
dell a525 speakers,balck, dim
dim c5521,a64 x2 5600+ 2.8GHZ)
13 in 1 media card reader, dim,s
16x dvd +/- cdrw drive,black,dim.s
256mb ati radeion x1300 pro,dim,s
4gb ddr2 sdram,667MHZ-4x1GB,dim,s
500gb sata II,7200RPM,dim,s
integrated audio (sigmatell high definition audio)
intergrated ethernet
----------------------------------------------------------------------------------------------------
thats what the product sheet says my computer has....

i also have the logitech dinovo keybord mouse and media pad combo which is bluetooth.
now here is what i have found.....

the computer came shipped to me with windows vista...a zune media player and a cyberpower backup battry for power outtages.

the computer in vista is great..though i don't like vista it's self...actually.....i hate it. >.<
i placed windows xp on here and well it only sees like 3.?? gig of my ram and about 175gb of my hard drive space...remember the hard drive is 500GB.

so i  tryed ubuntu on it.... now there are some major issues...there kinda a pain in the **** but they might be fixable? O_o

first the ati radieon x1300 Pro? forget about getting it ready...this is a low profile card...with a really weard connector on it....looks kinda like a DVI video port..untill you look at the y connector that connects to it then splits of into 2 seprate cables lable 1 2 for the dual monitor capibilitys for the card...no ati driver or other seems to be able to run this card under ubuntu...what junk XD.

then there is the sound issue..the audio card that is built into the computer..seems to produce sound rather well...but forget about trying to use the microphone...i eventually gave up and had to use the microphone on my logitech usb headset...

the dinovo keyboard mouse and media pad... ok it's good under windows...the buttons...like stop fast forwards and such includeing volume up and down... as well as the media pads lcd screen suck....no big surprise there...already researched it and logitec won't give out the code...and have no plans to do so in the future

the keys work well bluetooth syncs to the hub after pressing a few keys..but only after unplugging and repluging the usb bluetooth adapter.

my question is this:

im not back in vista and hate it..despise it really..i cannot get a return on my computer for the shiney new ubuntu systems that they have comeing out :(  and ubuntu seems stable if you use the onboard nvidia video card... 
should i honistly whipe windows off of here and put a copy of ubuntu on? i have the most current bios and my hardware is really good from what im told... i like ubuntu it is stable but for the error messages about the sound and the usb stuff with DEBUG in front of it.
should i dual boot? what should i do about the sound card and video card issues? 
i really want to keep what i payed for... 
or is it that the technology in this computer is state of the art and linux has to catch up with it?

has anyone else had issues like these? are they fixible without popping extra moneys for a sound card and video card?

other than those problems the computer rules..it's fast responsive and very small...at about 4 1/2 in wide 15 1/2 in tall and 13 1/2 in from front to back....

are there solutions? 

thanx for your time

---

### Post by hellmet on 2007-06-01
I suggest you keep Vista and enjoy it for a few days, since you've bought the computer with it. Meanwhile, try ironing out Ubuntu issues one by one. When you think you're ready, wipe Vista off !!

---

### Post by latepaul on 2007-06-04
Hi,

I bought a C521 from Dell Outlet a couple of months ago (though mine only had 2Gb, 320Gb and came with XP).

I got it, mostly due to the formfactor, as a cheap and easy way to build a MythTV box. 

I'm not an Ubuntu user but I had similar problems on both Fedora and OpenSuse. 

I struggled for a long time to get the X1300 to work. There are drivers from AMD but I went through various versions and still got "the black screen of death" (X hangs on startup with a blank screen). As an experiment I tried out the onboard Nvidia card (to enable it you need to remove the ATI card and change a setting in the Bios). It worked fine and was sufficient for my needs so I sold the ATI card on Ebay.

I never tried to use the microphone so I don't know about that.

The other problem is that there's a common problem with this motherboard and USB under Linux. You find that after a while your keyboard or mouse stops working. Some people find that plugging and unplugging fixes this. For me this usually doesn't work. Others found the problem was fixed when they upgraded the bios to 1.1.4 - which is the version my PC (and I guess yours) came with. Another solution apparently is to use an externally powered USB hub. I haven't resorted to spending more money yet but I may try that. It's annoying but I can live with it since most of the time I never touch the keyboard or mouse anyway.

Dunno if that helps at all.

Paul

---

### Post by pulivi on 2007-09-13
> **latepaul said:**
> Hi,

<snip>

The other problem is that there's a common problem with this motherboard and USB under Linux. You find that after a while your keyboard or mouse stops working. Some people find that plugging and unplugging fixes this. For me this usually doesn't work. Others found the problem was fixed when they upgraded the bios to 1.1.4 - which is the version my PC (and I guess yours) came with. Another solution apparently is to use an externally powered USB hub. I haven't resorted to spending more money yet but I may try that. It's annoying but I can live with it since most of the time I never touch the keyboard or mouse anyway.

Dunno if that helps at all.

Paul

Hi,
there is a very nice service on Dell support site to update the BIOS (latest is 1.1.10,
so your BIOS is old). About the hubs you're right, do not spend more money, after
upgrading the BIOS the only thing you have to do is to give the kernel the command
line "acpi=noirq" and you're done. C521 have problems with ACPI' managing IRQ lines,
this solves the problem as they have done under Windows, I suppose, with the updates
by nVidia, but this is confidential material ;-)

Just my 2c

---

### Post by morrisonpeter on 2007-09-23
"after upgrading the BIOS the only thing you have to do is to give the kernel the command
line "acpi=noirq" and you're done."

OK, I'm not a total noob, but for those of us who don't know, could you tell us how to give the kernel that command?

Thanks!

---

