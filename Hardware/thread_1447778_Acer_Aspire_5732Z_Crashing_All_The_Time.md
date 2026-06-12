---
title: "Acer Aspire 5732Z Crashing All The Time"
date: 2010-04-05
forum: Hardware
---

### Post by lonewaster on 2010-04-05
hi.
I just got a new Acer Aspire laptop ( great deal by the way >_< ) and instantly put Ubuntu 9.10 Karmic Koala on it (from an official Ubuntu 9.10 CD, coutesy of Canonical Ltd [thxmuch guys!])
Problem is, its always crashing.
Usually when im on Firefox, and out of the blue, boom. Freezes up and i can't use my window-crash force-closing thingy (added into my toolbar through the GUI screens)
Here is my lappy spec-

Intel Pentium Duo Core 2.20GHz T4400,
4GB RAM,
500GB HDD,
Acer Nplify 802.11b/g/n internal wireless.

it has loads of little things like 5-in-one card reader and inbuilt webcam but my old lappy had that stuff and NEVER crashed (unless i caused it lawl)
this is killing me because i just CANNOT live without my linux setup.
I have been tempted to just format and put a fresh install on, no partition, but wanted to check to see if anyone knew anything or had any ideas.
I've posted a bug report when it prompted me to do so...

please help if you can guys, i shalt love thee forever if thine help shalt work for mee :lolflag:

cheers,

-billy-
[lonewaster]

---

### Post by gordintoronto on 2010-04-05
Have you run the memory test from the CD overnight?

Is the CD 32-bit or 64?

Can you define "always crashing"?  Once an hour? Once a day?

---

### Post by lonewaster on 2010-04-06
up to 5 times a day. at least once.
the cd is 32BIT...wait...could that be it?
the laptop came with 64-bit win7 installed...i never took notice of the fact that the cd was 32-bit..
could that be the issue?
i **always** run the CD check before installing, and when i hand out CDs & convert people i **always  **teach them that you need to run a CD check first to make sure all goes well...i feel its good practice to teach people that because, if they are like my mum & dad, they just want a computer to "work" so if they think that its necessary then they will always do it, and teach others to do it.

i have run memory checks too, not from cd...just the automated ones on booting up the laptop after a crash.

i have started downloading ***ubuntu-9.10-desktop-amd64.iso*** from ubuntu.com, and am getting OK speeds so when it is done i will try formatting my lappy and putting the 64-bit version on.
i should've known better...i have my HNC computer architecture 1 unit(s)...lawl...anyways, if anyone has any idea as to why this might be happening, please elaborate.

thanks guys, 
it is because of the endless support obtainable from this community that makes me love ubuntu as much as i do.
there is no other OS with as much support and help as there is available here.

[COLOR=Magenta]**<3**[/COLOR]

---

### Post by gordintoronto on 2010-04-06
I would be amazed if the 64-bit install works any better than the 32-bit. Mind you, it is not the same, so it might.

The CD has a memtest program, which might be worth running for a while.

Here's a terrible suggestion: if you run Windows for a while, does it produce a "blue screen of death"? (I think that has actually changed with W7, but you know what I mean.) There are tools for figuring our what caused a BSOD, see the Network World site for details. (Windows stores information in its swap file, so it can be debugged. It helped me find some bad memory on my wife's machine)

---

