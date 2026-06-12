---
title: "LAN Card Messed Up"
date: 2010-10-16
forum: Hardware
---

### Post by JustinHD on 2010-10-16
Yesterday after I installed Ubuntu 10.10, about 1 hour later my network card stopped communicating with my router.

Basically my ISP provided me with a router in order for me to connect to the internet. It worked fine up till now. Suddently, the router's LAN LED stopped glowing and I was wondering why. It stopped working in both Windows 7 and Ubuntu 10.10.

I tried swapping the cable ends, changing the cable, even the router. Then I went to a friend and plugged my router in and it seemed to work on his machine. 

Then after some time of browsing around searching for a solution, I found out that setting my Speed & Duplex setting of my card to 10 Mbps Full Duplex made the card work with my router.

Any ideas why this would happen NOW? Is my card going to burn out eventually, is it a driver problem? OS problem (conflict) ?

I tried changing the driver but no avail.

---

### Post by dtfinch on 2010-10-16
I experienced this sort of issue two days ago on 10.04, with an onboard Realtek RTL8111/8168B, after almost 6 months of working fine. I haven't fixed it on mine yet. I assumed it was my card though and ordered another, since the LED was off when I plugged it into my router.

I probably should have investigated a bit more:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564984) (failing to autonegotiate speed)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259) (breaking card in Linux and Windows until power is turned off and back on)
[http://ubuntuforums.org/showthread.php?t=1436667](http://ubuntuforums.org/showthread.php?t=1436667)

---

### Post by JustinHD on 2010-10-16
Unfortunately I did all of those:
- i turned off my pc since then
- i tried setting 100 Mbps Full Duplex and it still didn't work
- i did not try unplugging everything from the wall socket just yet but i will do it in the next 10 minutes

Judging by the number of cases just like mine, i think the chances that my card is actually "dieing" are very slim and i tend to think that this is a software caused problem.

Still working on it. Will come with updates.

P.S. So far, Ubuntu 10.10 (from my noob point of view as i'm not that experienced with linux) is not a stable system.

---

### Post by JustinHD on 2010-10-16
Uhm....

Believe it or not...that did it. My LAN card is back to normal.

I unplugged everything from the wall socket, basically no power into the central unit and now my lan card is working like it did before. 100 Mbps Full Duplex in both Windows 7 and Ubuntu 10.10

I have no explanation whatsoever regarding to what happened or the solution for that matter.

I have to admit that I wouldn't have thought about this solution, not in a million years.

Should make this a sticky for other ppl out there.

Cheers,
Justin

---

### Post by dtfinch on 2010-10-16
That did it for me too. Simply turning it off and back on wasn't enough, but unplugging it worked.

---

### Post by Yellow Pasque on 2010-10-16
I guess the LAN card needed to be completely powered off to be reset and you have to unplug the PSU so you don't have standby power..
Mark solved please.

---

