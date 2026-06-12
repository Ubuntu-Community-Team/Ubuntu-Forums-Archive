---
title: "Trying to get suspend working properly on HP dv9000"
date: 2008-06-26
forum: Hardware
---

### Post by Iehova on 2008-06-26
Hi guys,

There are a few things not working properly with this particular laptop at the moment, but of those one I'd really like to crack is suspend. Now, the computer actually goes into suspend just fine, doesn't complain at all, so that's good, but numerous problems arise when I wake it up.

First of all, I get a series of complaints about USB along the lines of "usb 1-3: device descriptor read/64, error -32". As a result of this, USB stops working.

Secondly, my laptop has an atheros 5007AG wireless card, and I'm using a fairly recent version of the madwifi driver that was patched to work under x86_64 (although the problem was the same when I was using ndiswrapper previously). The laptop fails to connect to any wireless networks on resume, and no amount of modprobe -r-ing and modprobing ath_pci and ath_hal fixes the issue.

The most worrying complaint is that when I come to shut my computer down after having suspended, Ubuntu must fail to unmount the disk properly as I hear that painful "click!" of the disk's emergency unload. Not good.

If anyone has any idea of how to fix these myriad problems, I'll be very grateful.

Thanks,

---

### Post by bullseyeck on 2008-06-26
i have the same issue on my dv6000 any help would be appreciated

---

### Post by phidia on 2008-07-02
I realize this thread is almost a week old now, but I wanted to chime in on it. There is a howto for HP laptops [here]("http://ubuntuforums.org/showthread.php?t=793553&highlight=ndiswrapper+won%27t+resume+suspend") but resume from suspend is not working for me either. Some people like to recommend HP laptops for linux but I found too many problems in my experience with them. It would be interesting to find out what hardware is in the laptops that have these problems.

---

### Post by Iehova on 2008-07-03
That reminds me actually, originally the synaptics touchpad was not working either on resume, but I fixed that by specifying that it not be unloaded on suspend (in some configuration file somewhere, but I can't for the life of me remember where. ;))

It's unfortunate that no-one seems to have an answer to this conundrum.

---

### Post by phidia on 2008-07-03
> **Iehova said:**
> That reminds me actually, originally the synaptics touchpad was not working either on resume, but I fixed that by specifying that it not be unloaded on suspend (in some configuration file somewhere, but I can't for the life of me remember where. ;))

It's unfortunate that no-one seems to have an answer to this conundrum.

Is the file your referring to  /etc/default/acpi-support ?
Even editing that isn't a total solution it seems plus it's been hard for me to find a guide to use for editing that file.

---

### Post by Iehova on 2008-07-03
Indeed it is, and it turns out I was mistaken, I actually specified that it be unloaded. Either way, it works now, it's just the other things that don't...

---

### Post by phidia on 2008-07-03
> **Iehova said:**
> Indeed it is, and it turns out I was mistaken, I actually specified that it be unloaded. Either way, it works now, it's just the other things that don't...

There are, I've found through search, other unsolved threads on suspend with HP laptops (other brands too-I've definitely seen acer mentioned) 
I would like to know if there's some common denominator here. The HP laptop I've been trying to configure has a athlon TK-57 64x2 cpu, nvidia geforce go 7150M video card and an Atheros AR5007EG wireless card.
BTW I did notice that suspend worked in opensuse but the wireless card was impossible to get working in opensuse.

Iehova, Maybe we need a poll to find out how many people have had these issues and also poll for the hardware specs?

---

### Post by Iehova on 2008-08-26
Hi phidia,

My laptop has a different CPU (TL-60 IIRC) and video card, but the same wireless card, for which I'm using the madwifi drivers (although getting that supported was trouble enough as it is ;))

---

### Post by cespinal on 2008-12-08
bump

---

