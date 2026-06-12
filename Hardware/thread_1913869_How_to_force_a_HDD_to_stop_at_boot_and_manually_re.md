---
title: "How to force a HDD to stop at boot and manually reactivate it ?"
date: 2012-01-23
forum: Hardware
---

### Post by Swiss_Knight on 2012-01-23
Hi there, :p
I am a brand new user to this forum, but that's about a year I use Ubuntu 10.04.3 on my machine (and for as long a forum reader). I beg you to forgive me my English, if by chance it is too bad.
Anyway...

My question is about HDD. I have three on my system, two for data and faulty MS operating systems, and one small for my Ubuntu.
The thing is that I rarely make use of the two former. Except when I need to see a special file or write something there.

So, I'm searching for "something", which I could call a "tool" or a "command", no matter what, but something that is working well enough to make these two unused HDD stop. 

And what I mean by "stop", is that I want these hard drives to be really inactive : 0 rpm for the platters, read/write head at rest. This would have the advantage of a near 0 W power consumption, a little bit more silence, reduced inner case temperatures, usage time saving for these disks. 8-)

So, if it exists something to do or to tweak "at boot" to make these disks not turning on,  it would be the ultimate solution. But I feel like it's not possible... :?
So I'm asking to know how to do this at the boot of Ubuntu, automatically. 

Two other details ;
- I don't want some process to access the stopped disks. Never. I want to be the only one able to wake them up.
- I do want to wake them up if needed, and after, to turn them off again. 

Thanks !
Cheers from Switzerland.

---

### Post by grahammechanical on 2012-01-23
In my opinion the most practical way to do this would be to buy two very small physical on/off switches and pass the positive voltage wire to the hard disk through the switch.

This link shows the drive power wiring of IDE hard disks. Sata drives are different. I am trying to find a diagram for Sata disks.

[http://www.pcguide.com/ref/power/sup/partsDrive-c.html]("http://www.pcguide.com/ref/power/sup/partsDrive-c.html")

[http://www.allpinouts.org/index.php/Serial_ATA_(SATA,_Serial_Advanced_Technology_Attachment)]("http://www.allpinouts.org/index.php/Serial_ATA_(SATA,_Serial_Advanced_Technology_Attachment)")

Regards.

---

### Post by Grenage on 2012-01-23
I pondered the same thing, but always get worry about recommending such things; the Daily Wail loves headlines like:

"Forum advice leads to death, house fires, and orphaned children"

I have done as grahammechanical suggests, for various fans and connectors.  As long as your board supports hot-swap SATA, you'll be fine.  It's a neat solution, and your computer looks like a space shuttle dash! ;)

---

