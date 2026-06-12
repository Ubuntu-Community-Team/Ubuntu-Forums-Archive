---
title: "Review of my new laptop - mostly good, WiFi (Broadcom) interesting stuff..."
date: 2008-06-16
forum: Hardware
---

### Post by Jim March on 2008-06-16
So I got hands on a new lappy - a low-end Dell 1525 from Beast Buy.  It's now a true "Windows Virgin": never even booted Vista, went straight to Ubuntu.

$499 got me:

* Low-end Intel dual core Pentium, 1.7gHz.  VirtualBox 1.6.2 is recognizing the hardware virtualization extensions...

* Intel965 video (meh - 860ish fps in GLXGEARS, but is fractionally more solid in Compiz than the 945 - the 945 works best with two "panes" worth of "cube", the 965 is supporting a true cube.)

* 2gigs RAM, 160gig HD.

* DVD burner drive (incl. the double-layer spec to 8.something gig).

* 15.4" 1280x800 glossy screen.

* Pretty decent keyboard, normal Synaptics flatpad.

* Sweet ports layout: 4 USBs, 1 Firewire 400 (micro-size of course), Expresscard/54 slot, SD camera memory slot, dual headphone jacks plus mike port, Ethernet and modem, standard VGA out, S-Video, even a mini-digital video plug.  (Ethernet chipset is a Marvell 88E8040 per lspci.)

* Sound is Intel-based, internal speakers are weak but clear.

* The absolute worst built-in WiFi card ever.  A wretched horror of a freakshow...but it's not all grim...more on this in a bit.

I first tried loading Ubuntu Hardy 64bit.  Worked OK, but couldn't get the WiFi running for love or money.  Here's how bad it is: Ubuntu has a neat checkbox on/off system for "proprietary drivers" (non-FOSS).  Even with that turned off, the WiFi drivers still want to load, even though they can't do bupkis.  I found Windows-compatible drivers with an .INF file but in 64bit, I couldn't even get them to work in ndiswrapper.  In 32bit Ubuntu I could at least ndiswrap them but the range was pathetic and after a couple of days the blacklisted "WL" drivers came back from the dead and totally screwed me.

The WiFi card in question is a Mini-PCI Express, Dell part number 1395, chipset is Broadcom BCM4310.

This weekend I was working on upgrades for a friend's Dell 1501 lappy about a year old, taking him from Feisty to Hardy.  I feared his WiFi would suck as bad as mine; I was already shopping EBay for Intel-based mini-pci express cards.  But his worked like a champ - killer range, rock solid using Ubuntu's driver installs, proprietary firmware of course (shrug) but at least no ndiswrapper.

His Broadcom card was a Dell 1390, but pay attention here: chipset read "BCM4311" (more advanced model?  As if Dell went cheapo later?)

Okay...interesting tidbit, some months back his 1501 had been vandalized...screen literally stomped in while in a hotel.  Hotel paid for damage(!), he bought a new one, I transferred his stuff to it, pulled his old HD and mounted it external as a backup drive, meanwhile he still had the old one as a parts horse.

"Dude, lemme pull your WiFi card outta the carcass!"

Sure enough, five minutes with a screwdriver and a Dell 1390/BCM4311 card is in my rig and running flawlessly.  I could likely go back to 64bit with no problem.

Here's where it gets way cool:

Inside the new Dell 1525 lappy are THREE I kid you not mini-pci express slots.  Why three I have no idea: one extra makes sense for an internal Verizon/Sprint/etc. cellmodem, and I guess they figured WiMax was coming.  So they also wired FIVE antenna cords.  Two are used by the current WiFi card, two more appear to be additional WiFi antennas, one blue cord is probably for cellmodems and hence the wrong frequency for WiFi.

What this means is, it would be dead simple to drop in this card:

[http://www.intel.com/network/connectivity/products/wireless/wireless_n/overview.htm](http://www.intel.com/network/connectivity/products/wireless/wireless_n/overview.htm)

...which can be had online for about $35.  Can you say "draft N with three antennas"?  Oh hell yeah.

Other tidbits:

* CPU is socketed and easily accessible.  It appears I could hot-rod this baby down the road.  The socket type is a "Socket P", mentioned at:

[http://en.wikipedia.org/wiki/Socket_P](http://en.wikipedia.org/wiki/Socket_P)

The memory in there now is 533 spec, stock CPU is a T2370 "Pentium dual-core".  So I'd want to find a Core 2 Duo that has a 533 bus...let's see...nooo...this thing is not a true "Santa Rosa" type...so it looks like I'm maxxed.  Meh.

* Hard disk turned out to be a respectable Western Digital Scorpio 5400.  Not bad for a cheapo rig.

* Battery life is decent, about 2.5hrs.  Surprisingly it came with the 56watt/hr battery instead of the smallest grade.  A 90-something is available as an option, probably sticks out a bit...

* Zero signs of overheating so far.  Absolutely no need for a "fan pad".  Main heat vent is to the rear.  No obnoxious fan or disk noises, either.

* My external USB cellmodem (Verizon USB720, Qualcomm chipset) for some reason works WAY faster on this machine than my old Acer, even though I'm using the same software (wvdial script) and the same location.  I'm getting upwards of 1,600kbs down, 250-300 up per speedtest.net - that beats a lot of DSL connections.  I have no idea what the difference is between lappys - the old Acer was a single-core Celeron 1.6, 1.5gigs, ran Hardy just fine once the kernel got some updates...

Upshot:

Dell 1390 WiFi cards can be had for less than $15 on EBay.  Once at least that much repair is done to the ghastly WiFi system, this is a damned respectable machine for the price.  One advantage to a 1390 is, if you ever have to send it for warrantee repair they're likely not to notice the mod.  An Intel draft-N card is another matter :) but you could always swap the stock crap back in.

Everything else with the 1525 is totally solid, both in terms of software stability and physical rigidity.  I'd call this thing a good buy with minor hardware hacking needed probably for any Linux distro until the Broadcom support project catches up.  I would assume Ubuntu is already using the very latest stuff and that any other distro will fail big with a 1395/bcm4310 card...

(As of this writing a version with a 120gig drive is $550.  That's still a lot less than what they run off of Dell's site - mine at $500 priced to over $200 less than at Dell.com.  I would bet the 1525 will see more sale prices somewhere...)

Jim

---

