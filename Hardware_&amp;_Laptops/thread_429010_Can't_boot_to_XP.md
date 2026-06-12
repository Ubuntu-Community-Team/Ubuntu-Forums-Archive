---
title: "Can't boot to XP"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by sirbobbinhood on 2007-04-30
I don't know if this is laptop specific but it is on my laptop so here it goes. I just got this Compaq Presario v6305NR and I want to play around with a few different OSes so I installed XP Media Center Edition 2005 as my primary OS to use then i partition my HD with two more partitions one for Vista and the other for Ubuntu. When I installed Ubuntu everything went fine, but when i booted it up and went to launch XP it sayed it was trying to find chkdisk but it couldn't find it, I then loaded up Vista to see if I somehow deleted both of them but Vista boots fine, it just doesn't see my XP partition. When I load up Ubuntu though i can see the drive just fine and all the files in it... I have no idea what's going on or why it's visible only to Ubuntu. Any help would be much appreciated I'm going to try a system recover tonight when I get a chance

Hardware Specs:
AMD Turion64 x2 TL-50 1.6ghz
1 gig of DDR2 ram
128 megs of which is shared to the nvidia 6150 graphics card
100 gig HD

---

### Post by mijj on 2007-04-30
ah .. i'm new at this, but .. i had a similar problem when i set up ubuntu as a triple boot system with 2 XP installations.

The problem is:  when the grub boot manager is set up, it sees the Ubuntu partition and the two other OS partitions and sets up its configuration file (/boot/grub/menu.lst) accordingly.  So you see three boot options when you start up.

... however ... it doesnt take into account hiding and unhiding windows os partitions when setting up menu.lst - which is neccessary if there's more than one windows os partition.   (is this true if Vista is one of the Windows OSs? .. i'm guessing it is.)

the relevant windows partition needs to be "unhide"ed and the other windows partition needs to be "hide"ed for the chosen windows partition to boot up correctly.   the menu.lst, when it's originally set up doesnt add these lines automatically.


for instance .. the Windows OS parts of my menu.lst are ...
```

title		XP minimum
root		(hd0,0)
savedefault
hide		(hd0,1)     # the XP bloat partition
unhide		(hd0,0)
makeactive
chainloader	+1
#---------------------------------------------------------------------------
title		XP bloat
root		(hd0,1)
savedefault
hide		(hd0,0)      # the XP minimum partition
unhide		(hd0,1)
makeactive
chainloader	+1
```

i hope this helps.

---

