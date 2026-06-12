---
title: "Help, Can't install Breezy"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by m.musashi on 2006-02-02
Okay, granted I'm new but I've installed Breezy on several laptops (using one right now) and a few desktops. Now I'm trying to install on a new custom built compter and it's failure after failure. I suppose it's probably hardware incompatibility but I bought a nvidia chipset because they are supposed to support Linux well.

Anyway, here is the problem. Basically, it wouldn't install until I read about using nolapic noapic options and that did it but the xserver wouldn't load. Then I read about installing as a server and using apt-get to add the desktop. That did a nice install but upon reboot I get a bunch of errors as follows:

ACPI: unable to load the system description tables
PnPBIOS: resource structure does not contain an end tag
FATAL: Error inserting fan (/lib/modules/2.6.12-9-386/kernal/drivers/acpi/fan.ko): no such device
FATAL: Error inserting thermal (/lib/modules/2.6.12-9-386/kernal/drivers/acpi/thermal.ko): no such device
ALERT! /devb/hdc1 does not exist. Dropping to a shell!

Any idea what this is all about?

Another possible clue...When I boot the install CD with "server nolapic noapic" it will detect my network but still gives the above errors. If I just use "server" it won't configure my network.

Very frustrating. Any ideas?

UPDATE: well, apparently my issue isn't very interesting. I tried again with Dapper flight 3 CD hoping that maybe it had more recent drivers. It too crashes at various stages depending on what install option I choose. Install as a server results in similar errors as noted above and a non-working install. Install as OEM (maybe not the right choice but I'm just trying everything) freezes when it tries to download security updates (I don't think it's setting up networking and without a connection it just sits there). I haven't tried the regular install option yet but that will be next. However, I did try it earlier on a different drive and it didn't work then so I don't hold much hope.

Any help on this would be appreciated. I'm trying to be an Ubuntu user but it's getting frustrating.

---

### Post by el3ktro on 2006-02-02
Can you give some exact hardware info? With all this freezing & errors it seems something is really not right with your hardware configuration.

Tom

---

### Post by m.musashi on 2006-02-02
Oops. I seem to be cross-threading now. That was not my intention. I posted the other thread to just find out how to find out if my mobo was supported. Anyway, here are the vitals on my board:

- Support AMD Socket 939 Athlon 64FX / Athlon 64 X2 / Athlon 64
- NVIDIA GeForce 6150 + nForce 430
- Dual-channel DDR400
- PCI Express architecture
- Integrated GeForce6 GPU
- Dual VGA Ouput: DVI-D & RGB
- NVIDIA Gigabit LAN with NVIDIA ActiveArmor Firewall
- 4 x SATA II (RAID 0, RAID 1, RAID 0+1, RAID 5)
- 1394a Support
- High Definition Audio

---

### Post by WindowWasher on 2006-02-02
I have a very similar problem and have had no luck installing. I hope someone out there knows what's up because I'm lost in Ubuntu-land.

---

### Post by el3ktro on 2006-02-02
It just seems that you have a buggy ACPI. ACPI is really tricky, many mobos or BIOSes don't implement it correctly. Go into your BIOS setup and see if you have any ACPI settings that you can change, or try to do a BIOS update.

Tom

---

### Post by m.musashi on 2006-02-02
I have the most recent BIOS update. I actually just updated prior to my most recent attempts to install

You may be onto something. I had two options in my BIOS related to ACPI. I disabled one and Windows wouldn't load so I figured that wasn't a good thing. I disabled the other (something about ACPI 2.0 support) and Windows booted so I went ahead and tried a regular Ubuntu install. It went fine (much better than before) but upon reboot, when you get the brown Ubuntu logo and it starts to boot up) I crashes and sends me to a shell with a # prompt. I got all the same errors as above.

However, since it looks like it installed is there anything I can do from here to get it to work? What are the two drivers referenced in the above errors - fan.ko and thermal.ko? I don't have a working network connection so I can't download anything (i.e. it failed to set up during install).

Thanks again. I seem to be making progress...I think.

---

### Post by m.musashi on 2006-02-02
Also, what does the bit about "ALERT! /dev/hdc1 does not exist" mean? Isn't that my HD where Ubuntu is installed? How come it doesn't exist?

---

### Post by m.musashi on 2006-02-02
[QUOTE=el3ktro]It just seems that you have a buggy ACPI. ACPI is really tricky, many mobos or BIOSes don't implement it correctly. Go into your BIOS setup and see if you have any ACPI settings that you can change, or try to do a BIOS update.

Tom[/QUOTE]

Okay, yes. I've done a bit more research and ACPI is definately a problem. According to [http://quaggaspace.org/a8nvm/](http://quaggaspace.org/a8nvm/) there is a fix but I certainly don't have the skill to implement what he's suggesting (compiling a kernel and all). Howerver, I downloaded an ISO of Dapper which has the newer kernel that is recommended on in that link. I also turned off everything related to ACPI in my BIOS. Again, I get an install that drops to a shell but I'm getting fewer errors so maybe that is a good thing. Here is what I get now

> Booting the kernel.
[    13.536089] ACPI: Unable to load the System Description Tables
[    13.546546] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
ALERT! /dev/hdc1 does not exist. Dropping to a shell!


BusyBox v1.01 (Debian 1:1.01-3ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

Does anyone have any suggestions from here?

Also, how do make a suggestion to the developers to include this fix in the next release? Apparently it's an issue for more than just me.

Thanks.

---

