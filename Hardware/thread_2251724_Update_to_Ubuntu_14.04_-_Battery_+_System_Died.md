---
title: "Update to Ubuntu 14.04 - Battery + System Died"
date: 2014-11-06
forum: Hardware
---

### Post by kmast1212 on 2014-11-06
Hey guys,

Been using ubuntu on my old netbook (xp days), which I eventually put it down to xubuntu, since it ran alot smoother.
Wasnt using it for about 7 months, then decided to take it out for a spin. 
Tried booting to xubuntu = failed. Retried enough times to realise it just wasnt working.
Booted into the standard Ubuntu, which I think was on 12.04LTS, so I decided to let he update manager bring eveything up to speed.
Left it over night updating, but found it had halted about 3/4 the way through. Went to unplug the netbook and bring it down stairs, where it suddenly died.
Tried plugging it back n, rebooting, could't even reach the login screen...
So after a day or so, I booted WaryPuppy from a live usb, took my files off and then formatted the laptop and installed the latest Lubuntu.

Since the ubuntu update failure, the battery light on the netbook has been flashing orange (normally solid-green) and since then cant hold a charge.
Battery was perfect up until the attempted update and could hold a 1+1/2 hour charge. 

Now, in Lubuntu, its states 
Current Charge: 100%
Fully Charged Design 48.8Wh
Fully Charged 15.1WH

It cant be that the battery's gone kaput...so just wondering does anyone know what might be the problemo? 
Much appreciated!

---

### Post by Bucky Ball on 2014-11-06
Welcome. If it is an old laptop that hasn't been used for seven months there is no guarantee the battery was fine. They die, especially when not charged for a long time.

Take the battery out, plug the machine in to power adapter and give it a go. If the battery is dead it can prevent the machine from booting (some machines, not all, and that is from first hand experience. 

Laptop batteries need to be used and going though drain and recharge cycles to remain functional. Months of remaining flat they don't like. ;)

---

### Post by kmast1212 on 2014-11-06
Hey,
Yeah it works find when plugged in. And when I took it out of storage, it was on full charge, turned it on there and then without plugging it in.
Been snooping around the interwebs, and Im starting to think its a BIOS issue.. 
I just booted it there, and it told me that theress a bios issue regarding ACPI info.. Kinda thinking this is the issue..?


Also, if it is the BIOS thats causing the issue..is there a way of updating the BIOS from linux? Only guide I found says to boot into windows first.

---

### Post by Mike_Walsh on 2014-11-06
Hi, kmast.

I'll give you odds of 50-1 it IS the battery; and I'm pretty certain I'd collect... 

I have a very old Dell Inspiron 1100 laptop, which I've had since new, in 2002. About 2 1/2 yrs ago, I got the exact same issue as you; the battery charge light suddenly flashing orange very rapidly (instead of green). I'd nearly always used it on mains, ALL the time, and it rarely got used on battery alone; a silly thing to do, as, since Bucky Ball has pointed out, rechargeable batteries DO need regular drain and recharge cycles to remain in good condition.

(This laptop is a BRICK, compared to modern systems; the battery pack alone weighs more than a fully-kitted out Mac 'Air'...) But; it still works.

The former Ni-MH (nickel metal hydride) rechargeable batteries that were prevalent before the advent of lithium-ion cells used to develop a 'memory' problem, if they weren't regularly drained to the point of being flat and THEN fully charged. If they were constantly just 'topped-up', they would get to the stage where they would ONLY accept the small amount of charge they were used to getting...and there wasn't a thing you could do with them after that. It was entirely down to the battery chemistry.

Nowadays, with modern lithium-cobalt-oxide 'ion' cells not having this 'memory' problem, and being able to hold a charge for months at a time (the average quoted self-discharge rate is in the order of about 1.2-1.5% per month), many people now seem to think that they will hold a charge for ever; not so. Even with a lithium-celled battery pack, if it's not in regular use, it STILL needs a 'top-up' at least every three months, just to maintain condition. I know what I'm talking about here, as I have been working with rechargeable batteries of various different types for MANY years. The previous generation Ni-Cad (nickel cadmium) batteries were even worse in this respect.

I accepted that a nine-year old battery pack had reached the stage where it needed to be gracefully retired; it was a miracle it had lasted as long as it did! So I got a new one....a high-capacity one, which would hold nearly double the aH capacity. I now get something approaching 5-5 1/2 hours out of a full-charge (probably aided by the fact that the old girl is now running Lubuntu, after XP 'xpired'); it uses considerably less power, and is far kinder on system resources than ever before!

According to your figures, your battery is struggling to hold 30% of its design charge...

Forget messing about with your BIOS; I can almost guarantee it has nothing at all to do with the issue. It may take a little bit of tracking down on the web, but bite the bullet, and treat your machine to a new battery pack. It'll thank you for it. A dead laptop is just a pile of useless junk...but if it still works, then it's well worth keeping it in service for as long as you can. Kinder on the planet, too!

Regards,

Mike. ;)

---

### Post by MIJ-VI on 2014-11-07
How old is the CMOS battery?

---

