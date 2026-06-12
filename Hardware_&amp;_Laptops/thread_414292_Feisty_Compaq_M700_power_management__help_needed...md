---
title: "Feisty Compaq M700 power management  help needed..."
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by rebbi on 2007-04-19
Hi,

I'm a relative newbie to Linux, so please be kind.  :confused: 

I've been playing with Live CD distros for weeks and weeks, and have found Utuntu Feisty (7.04 final release) to work extraordinarily well on the rehabilitated Compaq M700 that I bought for mucking around with Linux.

It seems that Ubuntu isn't using ACPI or any power management back end (not sure if this is the correct term) on my machine. Indeed, during boot, some text scrolls by very quickly that says something about ACPI being disabled because the computer is too old (??) Yet, my impression was that ACPI **was** implemented on some other distros (like PCLOS). (At least the option to implement it was offered somewhere and not ghosted out.) :) 

Battery Charge Monitor does manage to show a percent charge, and the icon appropriately changes to the power plug or battery icon when I am running off of AC or battery. It also shows the percentage charge of the battery, but not the time remaining. And the battery monitor About window says "Legacy (non-HAL) backend enabled."

None of this would bother me, except that Suspend/Hibernate is hit-miss.  If I push the blue sleep button on the left side of the laptop next to the LCD, the computer does go into what looks like Hibernate: the screen goes black and after about 10 seconds and some hard disk activity, the HD spins down. The laptop will wake back up if  I press the same button (and only that button) again. Only bummer: it sometimes seems to wake itself back up for no reason!

In searching the community documents, I did come up with this here: [https://help.ubuntu.com/community/ACPIBattery?highlight=%28acpi%29](https://help.ubuntu.com/community/ACPIBattery?highlight=%28acpi%29)

And the ACPI web site does seem to offer a "corrected" file for the M700. Has anybody tried this kind of fix? Might it screw up my firmware or something permanently?

Thanks for your help, in advance,

SF

---

### Post by sudo_nym on 2007-04-21
Well, since HP bought Compaq, you can go there for ROM / BIOS / ACPI-related stuff.  That's what I ended up doing for this old Compaq Armada 1700.  The site will get very specific about make and model, so the closest pointer I can give you is;

[http://welcome.hp.com/country/us/en/support.html?pageDisplay=drivers](http://welcome.hp.com/country/us/en/support.html?pageDisplay=drivers)

From there you can enter any relevant details, and find the right ROMpaq / firmware upgrades for your particular machine.  You will need access to a Wintel box, to create bootable floppies from the downloaded .exe's [may support Linux for more recent models, but that was my experience with an Armada 1700].  By the way, the installer *only* makes a boot-floppy; won't do anything to the host machine, so you can download / launch that from anything that runs Windows, and make your boot-floppy there.

It might not fix your problem, but then again, it might.  When I booted from the ROMpaq floppy and had a look at my BIOS settings, I found some very odd settings...  Turns out one of the reasons I wasn't getting any sound was, the audio part of the Plug+Play ACPI interface was *disabled*!  Maybe the same for your power management settings.

You can also find some nice little tweaks in there, like setting the BIOS for higher energy conservation, when running off the battery.

Actually, these ACPI problems are a little surprising, because Xubuntu 6.10's the only Linux distro I've tried that could control the cooling fan properly [more important than it sounds; if your computer overheats, it will go for an emergency shutdown without warning, to protect itself].  But then, that's Edgy, not Feisty.

Hmm.  This post is getting too long, but I hope you find something useful in it.


Happy hacking,

Patrick.

---

### Post by rebbi on 2007-04-22
Patrick,

Thanks for the reply. I've downloaded the ROM pack already. Now all I need to do is fund a computer with a floppy drive!!!  :( 

Thanks for your reply!

Take care,

Steve

---

### Post by sudo_nym on 2007-04-24
> **rebbi said:**
> Patrick,

Thanks for the reply. I've downloaded the ROM pack already. Now all I need to do is fund a computer with a floppy drive!!!  :(

Oopse...  Well I do hope it helps, if you can get it working.

And come to think of it, since floppies have gotten so outdated now, maybe bootable service-pack type stuff like this should be in ISO format, so you can burn a bootable CD from that...  Maybe it already does.  Hard to say, since these are tools/upgrades for older hardware.

> Take care,

Steve

Thanks, you too,

Patrick.

---

### Post by rebbi on 2007-04-24
Well, I just found a floppy drive for the thing on eBay for 10 bucks with shipping; couldn't resist... :popcorn: 

Take care,

Steve

---

