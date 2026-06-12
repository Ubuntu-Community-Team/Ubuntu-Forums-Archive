---
title: "New motherboard?"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by volfro on 2006-11-18
Hola, fellow Edgy users.

For the last couple of weeks (basically since I upgraded to Edgy), my computer has been freezing and sometimes restarting at random. We're talking a hard lock. No mouse movement, no CTRL+ALT+BACKSPACE, no nothing. It seemed to be happening under heavy CPU usage, but it would occasionally happen while the machine was at rest, leaving me with a completely blank monitor even after moving the mouse and pressing buttons. Every time, if it doesn't reset itself, it requires a hard reset via PSU switch or holding the power button down.

My first reaction: blame edgy, or the installation media. I carefully burned a new copy and reformatted/installed, to no avail. Still got hard locks. Checked my HDDs, and they're fine. RAM's good too. PSU is brand new and not having any problems.

Took it to my boss' shop, and slapped the diagnostic card in it. Card tells me my motherboard or CPU is bad.

Great.

On one hand it's a bummer. This is my production machine. On the other, I'm excited, because I get to buy a new motherboard and CPU! This computer is like five years old and I've upgraded pretty much everything else except the CPU and case, so once this is done I'll basically have a new system. :)

So my question is this: I've never really done any major replacement of parts on a Linux machine. I should be able to just get a new mobo/cpu and slap it in and attach everything and turn it on, right? I've very little experience in the motherboard/cpu department, so any help is greatly appreciated here.

Also, do any of you more knowledgeable hardware people know of any good ATX motherboards that I can get on the cheap that play nice with Ubuntu? I need one AGP slot and maybe five PCI (PCI-E I don't need, however; SATA isn't necessary, either, I'm on all IDE). 

I'd also prefer something that can accept a dual-core processor, though I don't want to spend a ton of money here. My cap is $250-$300 for everything (I know, I'm cheap, but what can you expect from a starving artist). I could definitely cannibalize computers at the shop, but I'd rather have something new with a warrantee. Do any modern motherboards accept a normal, single-core CPU as well as something with more than one core? I'm thinking of future upgradeability here.

The same goes for the case. I'm pretty sure it's not a standard-size motherboard, so I'll probably be picking up a new case as well. Anybody have any good experience with any particular (cheap) case?

This computer is probably five years old, so it's high time it had some problems. It's an old e-Machines T2080, and if you're curious, its [spec sheet can be found at the e-Machines site]("http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T2080").

Thanks very much for any and all advice! I'm looking specifically for Linux-friendly hardware here.

v

PS: To recap, a list of requirements for easy reference:
[LIST=1]
[*]Motherboard or CPU is dying, so I'm going to replace 'em both since I can't be sure which is the problem, and since the CPU is old/slow anyway
[*]Tips on good motherboards which can accept single AND dual-core processors (for the sake of upgrading in the future, once multi-core is cheaper)
[*]Any suggestions on CPUs that are cheap? (This one I wouldn't mind pulling off of one of the dead machines at the shop. Plenty of beefy CPUs there to go around.) I've had good experience with this Athlon, so I'd prefer to stick with AMD, unless somebody suggests otherwise.
[*]Any suggestions on good, cheap cases, preferably with external USB ports?
[*]All within the $250-$300 range?
[/LIST]
Thanks again!

---

### Post by pay on 2006-11-18
I would personally go with an Nforce mainboard with an am2 socket.

---

### Post by volfro on 2006-11-18
Why do you say that?

---

### Post by pay on 2006-11-24
I've used Nforce for awhile and haven't had troubles with them.

---

### Post by amp_man on 2006-11-24
Yep, definately agreed. I love my msi k8n neo2 platinum, which is an nforce3 board. I thought nforce 4 was pci-e only though, ie no agp?

---

### Post by volfro on 2007-01-31
I actually ended up getting an ASUS board on Newegg. It came with a PCI-E Nvidia Geforce 6400 gfx card AND an Athlon 64 cpu. Seemed to be a great value for the money, even though a few people reported problems with the RAID drivers in Windows. I figured, this isn't for a Windows machine, so that doesn't really matter. Sure enough, Edgy automatically detected and installed RAID capabilities.

Also, the on-board audio works near-flawlessly, which is a HUGE improvement over my previous experience with Linux and various sound cards.

Thank you all for the tips, though. I'll keep nforce in mind for when I need to upgrade again.

---

