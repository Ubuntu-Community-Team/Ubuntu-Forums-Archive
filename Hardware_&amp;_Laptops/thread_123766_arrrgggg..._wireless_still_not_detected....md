---
title: "arrrgggg... wireless still not detected..."
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by nalmeth on 2006-01-30
Ok, I'm starting to get pretty pissed off right here!

I've been at it for a long time with this Sony Viao laptop, and it is quite a stubborn soandso. 

I have a D-Link DWL-G650 wireless card, proven to be in working condition. This card is quite certainly supported by Ubuntu, and is usable with ndiswrapper aswell, or so I've heard... The problem (as some of you might have heard from my persistent complaining) is that the card is not detected by the laptop. 

Recently I found out that this laptop was using its original BIOS, and that many upgrades were available. I understand sometimes hardware problems such as this can be caused by an outdated BIOS. Well I flashed in the new one. Things are actually running noticebly faster, and my battery takes 15 minutes of inactivity to die rather than the 10 minutes it took before.

But, as you might have guessed, the wireless card is still, not, picked, up......
It's really actually quite frustrating! :-| 

I have tried other routes to find out what the problem could be, and all have come up with nothing. My last lead is some of the output of dmesg:

.....
.....
{4294672.323000} PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report.
bunch of things reserved, and others can't be reserved
.....
.....
initializing cryptographic API
PCI: Disabling Via external APIC routing
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
EISA: Cannot allocate resource for EISA slots 1, 6, 7
EISA: Detected 0 cards.
8139cp: pci dev ... ... ... is not an 81 39C+ compatible chip
8139cp: Try the 8139too driver instead
8139too Fast Ethernet driver ...

I'm sure some of this means nothing, but I included it anyway. pci=routeirq didn't change anything that I noticed, but I don't know what it was supposed to do anyway.

Can anyone translate this input into any info about my wireless related hardware? Or offer any other means of probing hardware (have run lspci, lshw, no card showing)? Or can anyone offer any other suggestions at all? Even the most far-fetched unlikely idea is better than what I have now --> NOTHING!

please please please, and thank you!

](*,)

---

### Post by heimo on 2006-01-30
[quote=nalmeth]Or can anyone offer any other suggestions at all? Even the most far-fetched unlikely idea is better than what I have now --> NOTHING!
[/quote]

Put *noapic* parameter on the *kernel *line in file */boot/grub/menu.lst *and reboot. No idea if it could have positive or negative effects, but I'd try that one too.

---

### Post by nalmeth on 2006-01-30
thank you for suggestion.

where exactly should noacip go? Below the "BEGIN AUTOMAGIC KERNELS LIST"? I imagine it is important that I don't just throw it anywhere, so I want to be sure its in the right place

---

### Post by heimo on 2006-01-31
[quote=nalmeth]thank you for suggestion.

where exactly should noacip go? Below the "BEGIN AUTOMAGIC KERNELS LIST"? I imagine it is important that I don't just throw it anywhere, so I want to be sure its in the right place[/quote]

You have entries like this in menu.lst, put noapic (not noacip) on the same line - at the end of the line which begins with word *kernel*. Example:
```
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash **noapic**
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

```

---

### Post by nalmeth on 2006-01-31
and thank you for clarification!

laptop booted up with no problems, but stopped for a period of time on "Waiting for network interface to come up" 
I can't tell if it made any other difference though. lspci shows same output as before, and no wlan is showing in networking.

Any way to see what changed from what we did? Any other tricks up your sleeve?

---

### Post by mpvano on 2006-01-31
I'm not sure what version VAIO you have, but some of them used to be very fussy about which slot cardbus cards were put into. In fact some of them only had ONE cardbus slot. I presume you've tried both slots? If not, try the other one.....

By the way, I presume when you say the card is known to be working, you mean it's known to be working in another machine. Is it possible it's a cardbus card and your notebook doesn't support them? Cardbus and PCMCIA are two different specs, even though the slots look the same. They're supposed to be compatible, but that only works one way - upwards.

If your card requires cardbus HW and your notebook doesn't support it, that's definitely a show-stopper. PCMCIA cards are basically a variation on the old ISA bus 0 but cardbus cards are essentially PCI cards in a different form factor with hotplugging. I believe they also take different power supply voltages from a different pin on the cardbus. This means that if your notebook doesn't support cardbus your card just sits there and doesn't respond to any poking or prodding at all....

Hope this isn't your problem, but you asked for other possibilities....

Mario

---

### Post by nalmeth on 2006-01-31
Yes thank you for adding that Mario. Anything you can, as I said.
The model of the Vaio is PCG-FX215
Yeah, I've tried both slots, and rolled snake-eyes.

Now I don't know much at all about wireless, but I believe the 2 ports are what shows up as:

0000:00:0a.0 CardBus bridge: Texas Instruments PCI1420
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1420

In the meantime of trying to get it going on this laptop, I tried the card on another machine and it is indeed in working order.
The laptop was used originally with windows, and presumably the wireless was working, the laptop had the card in the slot when I got it. Aparently someone (a pretty knowledgeable linux user) had tried to install Hoary on it, but was stopped at wireless aswell.

Does this bring anything to light?

---

### Post by LoclynGrey on 2006-02-11
Dude, i got one of those D-link cards but on a Copaq Evo N620c laptop.
Errrr sorry its not working yet so i cant shed anylight on the issue.
However if it means anything, you are not alone with this problem.

I did post about it and some one told me to start here.
------
[http://lists.debian.org/debian-lapto.../msg00068.html](http://lists.debian.org/debian-lapto.../msg00068.html)
If it's the same chipset, try the driver at [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)
-------

---

### Post by mpvano on 2006-02-12
Sounds like it's working but not connecting to the network. Usually the bootup delay is while it tries to get an address by DHCP, or tries to set the clock and gets no reply until a timeout.

Do you see the card and/or access point if you do:

sudo iwconfig

The sudo is important or you may not get all the information iwconfig has about the card and access point.

If you see the card listed, hopefully with the ESSID of the access point, then the problem is probably with the wireless settings. I've found the gnome networking applet and network configuration tool to be a little unreliable, so I set these things into /etc/network/interfaces manually myself. Look up the man pages for "interfaces" and "iwconfig" for the options you have here.

It can be very hard to associate with the right access point if you are somewhere that has overlapping coverage from more than one unless you specify the access point with the wireless-essid command. I also have to add a wireless-mode command and wireless-key line as well myself....


Mario

---

### Post by WolfJay_83 on 2006-02-12
I have a D-Link DWL-650.
With the repository version of ndiswrapper, I had to fight with the card to get it to even connect and when it did, it often lost the connection.  Reconnecting often resulted in a complete unrecoverable lockup.

What I found was that the repository version is much older (1.1 as apposed to 1.8) than the current version. So I followed the instructions on the wiki to install ndiswrapper from source. It has worked flawlessly since.

Note: do not use the drivers on your CD, follow the instructions on the wiki, and use the list of drivers for specific cards. 

Does your card have lights? mine has two: no lights = no drivers, one light= no connection, two lights= working.

Here is the link for the wiki page. [https://wiki.ubuntu.com/WifiDocs/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto#head-43b2e2295bcf52aef4217347410f0c605a5c1c0e]("https://wiki.ubuntu.com/WifiDocs/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto#head-43b2e2295bcf52aef4217347410f0c605a5c1c0e")

Hope this helps

---

