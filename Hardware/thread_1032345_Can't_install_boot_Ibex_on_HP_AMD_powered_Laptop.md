---
title: "Can't install/ boot Ibex on HP AMD powered Laptop"
date: 2009-01-06
forum: Hardware
---

### Post by iainfarrell on 2009-01-06
hi there

Like most hardware troubles people I'm trying to install for the first time having had success with virtual machines. Every time I try to install or boot either from a successful in Windows install or live boot I get the second loading screen with the orange bar that fills up. It gets 3/4 of the way through the third block and freezes - very early for a freeze. 

Can anyone help me debug this?

Specs are
AMD Athlon X2 Dual Core Processor QL60
(1.9GHz, 1MB Cache)
Genuine Windows Vista (R) Home Premium
2GB Memory
120GB Hard Drive
15.6" Screen Size
DVD Super Multi Double Layer
Nvidia Geforce 8200 Graphics
3X USB
Wireless Enabled

I'm trying to use the 64bit ISO and downloaded only the other night. I think the disk is fine as it passes the windows checksum when installing from there.

---

### Post by iainfarrell on 2009-01-06
See screenshots

It gets to this point in the verbose version of startup

[ATTACH]98919[/ATTACH]

Then it pauses, seems to dump information and then I see this

[ATTACH]98920[/ATTACH]

---

### Post by iainfarrell on 2009-01-06
Have also tried adding breaks to the install and a break before the bottom scripts are run (break=bottom) gives me a command line. Any ideas what's trying to run after that and failing so I can comment it out?

---

### Post by l_synapse_l on 2009-01-06
Try booting with kernel options -

acpi=off pci=nomsi

---

### Post by iainfarrell on 2009-01-06
Thanks for that suggestion, I think we're making progress

using the kernel options acpi=off pci=nomsi I get the attached screen. It pauses here for a few minutes and on first attempt then failed and gave me a huge dump of data as before. 

thoughts? :)

[ATTACH]98945[/ATTACH]

UPDATE - it's been a good 10 mins since I tried a second time and it's just hanging ... plot thickens

---

### Post by iainfarrell on 2009-01-06
One more thing occurs to me, I'm getting a lot of I/O errors and I wonder if those are caused by the odd partitioning of the drive. It's divided about 100gb - 20gb allowing the 20 for a full backup install of Windows Vista. Red herring or issue?

---

### Post by duds2008 on 2009-01-06
As iainfarrell says try disabling acpi. The way I do it (and this has worked on 6 seperate PCs/laptops) is by adding the boot parameter acpi=off noapic. If you have display problems you could also add vga=771. If it is an IDE HD you could also add generic.all_generic_ide=1.
Hope this helps.:)

---

### Post by quip on 2009-01-06
I don't think this is your issue, but if you have a wireless "kill" switch on your laptop (the kind that disables it completely), you could try turning it off and seeing if you could boot up.

Both times, it seems to be having a problem loading the driver for your Atheros wireless adapter.  That's odd, because Atheros is pretty well supported on Linux.  I have had two laptops with them.

Again, I don't think it is the issue, but it would be something simple to do, and it has appeared right before your freeze both times...

---

### Post by iainfarrell on 2009-01-07
Oddly enough just tried a Suse Live CD and it works fine ... wonder what could be different. Do they use different wireless drivers?

---

### Post by iainfarrell on 2009-01-07
The Linlap wiki has some insight I think. 

[http://www.linlap.com/wiki/hp+pavilion+g60](http://www.linlap.com/wiki/hp+pavilion+g60)

Suggests

"Do not configure during installation. Post installation configuration identifies Atheros driver"

I'm trying to go down the Suse route at the moment but is there a way to disable wifi during installation?

Also, does Ubuntu have the same issue with licensing of NVidia drivers for the graphics as Suse?

---

### Post by quip on 2009-01-07
> **iainfarrell said:**
> Oddly enough just tried a Suse Live CD and it works fine ... wonder what could be different. Do they use different wireless drivers?

It depends.  The two distros could recognize the card differently, and then try to load two different drivers, but they are all using the same drivers in the end.

The newest Atheros drivers use the newly-released open source Atheros drivers (or at least HAL was open sourced), while older chipsets often use the older ath_pci module.

If you used openSUSE 11.1, it might have a slightly newer kernel then your Ubuntu version.  The opposite proved true with me; a couple of months ago, I tried to put 11.0 (the newest at the time) on my new laptop, since I had been using openSUSE for a while.  It didn't work, even when I built wireless-modules by hand.  However, the drivers got mainlined by 2.6.27, and I saw that Ubuntu 8.10 shipped with that, so I installed Ibex and all was good.

It just depends sometimes...

---

### Post by iainfarrell on 2009-01-08
Success!! Different CD and an image of the 32bit instead of 64bit and it worked fine! I now have a lovely 8.10 system. Although, it crashes on suspend but a small price to pay!

---

