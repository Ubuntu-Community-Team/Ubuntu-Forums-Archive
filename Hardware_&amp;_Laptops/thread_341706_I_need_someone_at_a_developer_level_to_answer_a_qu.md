---
title: "I need someone at a developer level to answer a question"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by ExploreMN on 2007-01-19
Can anyone who is a true Linux master...someone at the level of the developers, high level programmers, etc....please explain to me why no linux distro on the fricken planet supports the SiS965L chipset?

I've tried the latest and greatest of all the big linux players out there and none of them work. Upon further investigation I am finding that there are MANY frustrated users out there in the same boat as me.

So what is the hang up? Why is this particular, yet frighteningly popular, chipset so avoided, shunned, and just plain not developed for?

I'm just really frustrated because I've spent a good $475 total building what was supposed to be an awesome PVR only to realize I am sitting on a piece of crap that only Microsoft seems smart enough to support. So I'm forced to either spend MORE money or just give up on Linux and stick with Microsoft.

---

### Post by Hendrixski on 2007-01-19
Well, it's kind of new, and the only drivers for it now are proprietary drivers created by SIS.  You can download them here: [http://www.dirfile.com/sis_raid_driver_for_linux_kernel2_6_10__v2_6_10_1_00_00.htm](http://www.dirfile.com/sis_raid_driver_for_linux_kernel2_6_10__v2_6_10_1_00_00.htm) ... just scroll down past the crappy advertisements at the top of the page, and there's a driver and instructions on how to install it.  That should make any distribution work with the SIS965L chipset. 

hope that helps

---

### Post by ExploreMN on 2007-01-19
I actually found those drivers, but I tried to follow the instructions and they don't work. I tried doing it off the Ubuntu LiveCD and came up with a whole slew of errors that look as if the includes needed are not available.  I'm on my laptop right now which has Ubuntu installed and when I type "make" here it doesn't even recognize the command.

So if it is new, roughly how long will it be for linux to catch up and actually have the drivers as part of their builds?

---

### Post by blackened on 2007-01-19
I'm usually not one to play the "if you need it so badly then develop it yourself" card. No Linux developer is obligated to write software. Period. None of these people owe you or me anything. We don't pay them in anything other than gratitude (and some of us don't even do that much). So, while I understand your frustration, isn't compatability something you should've checked before buying?

---

### Post by mcduck on 2007-01-19
> **ExploreMN said:**
> I actually found those drivers, but I tried to follow the instructions and they don't work. I tried doing it off the Ubuntu LiveCD and came up with a whole slew of errors that look as if the includes needed are not available.  I'm on my laptop right now which has Ubuntu installed and when I type "make" here it doesn't even recognize the command.

So if it is new, roughly how long will it be for linux to catch up and actually have the drivers as part of their builds?

Then just get the dependencies, and if you need to compile something install the 'build-essential'-package too.

Writing drivers for hardware is hardware manufacturer's job, not OS developer's. If you have problem with their drivers then you should give them feedback about it.

---

### Post by ExploreMN on 2007-01-19
> **blackened said:**
> I'm usually not one to play the "if you need it so badly then develop it yourself" card. No Linux developer is obligated to write software. Period. None of these people owe you or me anything. We don't pay them in anything other than gratitude (and some of us don't even do that much). So, while I understand your frustration, isn't compatability something you should've checked before buying?
I try not to view Linux in this manner because it is somewhat of an attitude that it is still a "hobbiest" operating system, but I think it has grown beyond that and should be treated with a little more regard than just a "do it yourself" attitude. Furthermore, Linux is becoming more and more of an "everyone" operating system, but as such, it needs to be able to be dumbed down for the masses that don't have the time, energy, capacity, or desire to learn programing or other high level, behind the scenes Linux administration.

Anyway, sorry to rant...

---

### Post by blackened on 2007-01-19
> **ExploreMN said:**
> I try not to view Linux in this manner because it is somewhat of an attitude that it is still a "hobbiest" operating system, but I think it has grown beyond that and should be treated with a little more regard than just a "do it yourself" attitude. Furthermore, Linux is becoming more and more of an "everyone" operating system, but as such, it needs to be able to be dumbed down for the masses that don't have the time, energy, capacity, or desire to learn programing or other high level, behind the scenes Linux administration.

Anyway, sorry to rant...

Then in the same vein it would be prudent to only buy hardware that is known to be currently compatible with Linux and then write the competing manufacturers and explain your decision.  Most hardware problems in Linux are caused by manufacturers not releasing open documentation for their hardware, and this problem is not simply going to disappear if we, as consumers, continue to invest in a hardware infrastructure that does not care about its customers' needs.

---

### Post by ExploreMN on 2007-01-19
So how can you find out before hand if it is compatible? Is there a magic list someplace that perhaps you could share with me? It took me almost a week of doing constant and intensive searching...not to mention countless hours of downloading and trying different distros just to find out this particular chipset/motherboard is not compatible.

Basically, I am now in a position to find a MicroATX motherboard with a PCI-Expressx16 slot...preferably socket 754 (AMD) that is compatible so that my loss is a minimum on this project. I've tried doing "chipset" searches, but unfortunately that always comes up with multiple hits for problems when doing a search for "<chipset> linux compatability"

---

