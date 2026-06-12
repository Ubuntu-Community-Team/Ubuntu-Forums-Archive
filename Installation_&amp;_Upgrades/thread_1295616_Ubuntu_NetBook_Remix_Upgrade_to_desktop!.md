---
title: "Ubuntu NetBook Remix Upgrade to desktop!?"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by babygirlxoxo on 2009-10-19
Okay i have windows xp home edition, i than downloaded ubuntu netbook remix and saved it to a usb and than reformatted my hard drive and installed ubuntu netbook.. i seriously do NOT like this one, everything is kinda of scattered and messy, half of the programs most people use arent capatiable.. i either wanna put windows xp back on my usb stick, or put ubunto desktop 9.04 i think its called, well i can't do either, because the program unetbootin or whatever it is called. I downloaded the ver for linux, and  i can't install it, it says its not capatiable, if so, than why do they have a linux download for it , if it doesn't even work, i really need this to put my desktop ver on my usb stick. I've been searching google, and forums but i can't find anything that fully answers my questions, keep in mind im very new at this, also once i figure out have to do that i still need a probram to check the m5sum .. idk if they have one for my ubuntu.. can anyone help?

---

### Post by earthpigg on 2009-10-19
hi,

> I downloaded the ver for linux, and i can't install it, it says its not capatiable.... half of the programs most people use arent capatiable

i think i see the root of your problem.

in Linux, we don't generally download software from websites. we use the [package manager]("http://en.wikipedia.org/wiki/Package_manager") to get it from [software repositories]("http://en.wikipedia.org/wiki/Software_repository"). 

click around for "add/remove programs" or "synaptic package manager". 

search for unetbootin there.

another way you can easily put it on a thumb drive is ubuntu's "USB Startup Disk Creator". i don't know where this icon will be in the netbook remix -- maybe 'administration' or something like that?

---

### Post by earthpigg on 2009-10-19
unless you have a very good reason, avoid downloading software from websites at all costs.

the fact that Linux user's dont do this is one part of why Linux user's dont bother with antivirus software.

---

### Post by babygirlxoxo on 2009-10-19
Thanks so much i just installed it, you really helped me i don't know why they didn't put that in the instructions unless im blind and didnt see, i'm about to try and do it now, another questions, how do i format a usb through ubuntu? i know for windows you right click, format, FAT32 .

---

### Post by earthpigg on 2009-10-19
install 'gparted' using the methods described above.

then, system -> administration -> partition editor.

for a thumb drive, stick with FAT32.

(or perhaps you can just open it in the file manager and delete everything...)

---

