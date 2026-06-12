---
title: "d600 failing to boot on occasion"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by svguy on 2007-12-04
I've recently been trying to figure out why sometimes on resume my dell d600 fails to detect my network card. I used the information in this thread
[http://ubuntuforums.org/showthread.php?t=461294](http://ubuntuforums.org/showthread.php?t=461294)
and created a script that seemed to have fix the problem, until tonight. But that's another issue.

What started happening just last week was that occasionally on boot before i even see the bios screen i'd get two beeps and a black screen, and a flashing num lock light.  A tap of the power button turns it off, and another tap boots it up again, although a much slower load through bios.

Tonight, i clocked out at work, put the laptop in hibernate and drove home.  When i got home i let it sit for a few hours.  When i went to turn it on i got two beeps, and a flashing num lock.  Turned it off and turned it back on, and it turned itself off. Turned it back on again, slow bios load, and the computer came on.
When it finally loaded no network device was detected, and the script wasn't working.  
I restarted, at which point after the bios screen it said "press f1 to continue or f2 to go in to setup."  I went in to setup just for giggles and didn't see anything.
My search for dell beep codes hasn't turned up anything for two quick beeps, and i'm worried that something's going terribly wrong here and will only get worse.

I copied the most recent part of the /var/log/messages file. Can someone please help me with this? I'm a huge linux n00b.

> Dec  4 20:05:47 wabbit kernel: [ 4003.528000] swsusp: Basic memory bitmaps creat
ed
Dec  4 20:05:47 wabbit kernel: [ 4003.528000] Stopping tasks ... done.
Dec  4 20:05:47 wabbit kernel: [ 4003.732000] Shrinking memory...  ^H-^H\^H|^H/^
H-^H\^H|^Hdone (63406 pages freed)
Dec  4 20:05:47 wabbit kernel: [ 4013.668000] Freed 253624 kbytes in 9.93 second
s (25.54 MB/s)
Dec  4 20:05:47 wabbit kernel: [ 4013.668000] Suspending console(s)
Dec  4 20:05:47 wabbit kernel: [ 4013.900000] sd 0:0:0:0: [sda] Synchronizing SC
SI cache
Dec  4 20:05:47 wabbit kernel: [ 4013.900000] pnp: Device 00:0c disabled.
Dec  4 20:05:47 wabbit kernel: [ 4013.904000] pnp: Device 00:0b disabled.
Dec  4 20:05:47 wabbit kernel: [ 4013.904000] ACPI: PCI interrupt for device 000
0:00:1f.5 disabled
Dec  4 20:05:47 wabbit kernel: [ 4013.904000] ACPI: PCI interrupt for device 000
0:00:1f.1 disabled
Dec  4 20:05:47 wabbit kernel: [ 4013.920000] ACPI: PCI interrupt for device 000
0:00:1d.7 disabled
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] ACPI: PCI interrupt for device 000
0:00:1d.2 disabled
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] ACPI: PCI interrupt for device 000
0:00:1d.1 disabled
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] ACPI: PCI interrupt for device 000
0:00:1d.0 disabled
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] Disabling non-boot CPUs ...
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] swsusp: critical section: 
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] swsusp: Need to copy 60843 pages
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] ACPI: PCI Interrupt 0000:00:1d.0[A
] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] usb usb1: root hub lost power or w
as reset
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] ACPI: PCI Interrupt 0000:00:1d.1[B
] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] usb usb2: root hub lost power or w
as reset
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] ACPI: PCI Interrupt 0000:00:1d.2[C
] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Dec  4 20:05:47 wabbit kernel: [ 4013.936000] usb usb3: root hub lost power or w
as reset
Dec  4 20:05:47 wabbit kernel: [ 4013.952000] ACPI: PCI Interrupt 0000:00:1d.7[D
] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Dec  4 20:05:47 wabbit kernel: [ 4013.952000] usb usb4: root hub lost power or w
as reset
Dec  4 20:05:47 wabbit kernel: [ 4013.952000] ehci_hcd 0000:00:1d.7: debug port 
1
Dec  4 20:05:47 wabbit kernel: [ 4013.956000] ACPI: PCI Interrupt 0000:00:1f.1[A
] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Dec  4 20:05:47 wabbit kernel: [ 4013.956000] ACPI: PCI Interrupt 0000:00:1f.5[B
] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Dec  4 20:05:47 wabbit kernel: [ 4014.128000] ata1.00: configured for UDMA/100
Dec  4 20:05:47 wabbit kernel: [ 4014.128000] sd 0:0:0:0: [sda] 58605120 512-byt
e hardware sectors (30006 MB)
Dec  4 20:05:47 wabbit kernel: [ 4014.128000] sd 0:0:0:0: [sda] Write Protect is
 off
Dec  4 20:05:47 wabbit kernel: [ 4014.128000] sd 0:0:0:0: [sda] Write cache: ena
bled, read cache: enabled, doesn't support DPO or FUA
Dec  4 20:05:47 wabbit kernel: [ 4014.448000] ata2.00: configured for UDMA/33
Dec  4 20:05:47 wabbit kernel: [ 4014.968000] ACPI: PCI Interrupt 0000:01:00.0[A
] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Dec  4 20:05:47 wabbit kernel: [ 4014.968000] Yenta O2: res at 0x94/0xD4: 00/ea
Dec  4 20:05:47 wabbit kernel: [ 4014.968000] Yenta O2: enabling read prefetch/w
rite burst
Dec  4 20:05:47 wabbit kernel: [ 4014.996000] pnp: Device 00:0b activated.
Dec  4 20:05:47 wabbit kernel: [ 4015.044000] pnp: Device 00:0c activated.
Dec  4 20:05:47 wabbit kernel: [ 4015.624000] sd 0:0:0:0: [sda] Starting disk
Dec  4 20:05:47 wabbit kernel: [ 4015.696000] Restarting tasks ... done.
Dec  4 20:05:47 wabbit kernel: [ 4015.764000] swsusp: Basic memory bitmaps freed
Dec  4 20:05:47 wabbit kernel: [ 4015.764000] usb 1-2: USB disconnect, address 3
Dec  4 20:05:47 wabbit kernel: [ 4016.756000] usb 1-2: new full speed USB device
 using uhci_hcd and address 4
Dec  4 20:05:47 wabbit kernel: [ 4016.956000] usb 1-2: configuration #1 chosen f
rom 1 choice
Dec  4 20:05:47 wabbit gnome-power-manager: (courtney) Resuming computer
Dec  4 20:05:58 wabbit kernel: [ 4029.800000] tg3.c:v3.77 (May 31, 2007)
Dec  4 20:05:58 wabbit kernel: [ 4029.800000] ACPI: PCI Interrupt 0000:02:00.0[A
] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Dec  4 20:05:58 wabbit kernel: [ 4029.800000] ACPI: PCI interrupt for device 000
0:02:00.0 disabled
Dec  4 20:05:58 wabbit kernel: [ 4029.800000] tg3: probe of 0000:02:00.0 failed 
with error -5
Dec  4 20:05:58 wabbit kernel: [ 4029.864000] ieee80211: 802.11 data/management/
control stack, git-1.1.13
Dec  4 20:05:58 wabbit kernel: [ 4029.864000] ieee80211: Copyright (C) 2004-2005
 Intel Corporation <jketreno@linux.intel.com>
Dec  4 20:05:58 wabbit kernel: [ 4030.264000] ipw2200: Intel(R) PRO/Wireless 220
0/2915 Network Driver, 1.2.0kmprq
Dec  4 20:05:58 wabbit kernel: [ 4030.264000] ipw2200: Copyright(c) 2003-2006 In
tel Corporation
Dec  4 20:05:58 wabbit kernel: [ 4030.268000] ACPI: PCI Interrupt 0000:02:03.0[A
] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Dec  4 20:05:58 wabbit kernel: [ 4030.268000] ipw2200: Detected Intel PRO/Wirele
ss 2200BG Network Connection
Dec  4 20:05:58 wabbit kernel: [ 4030.480000] ACPI: PCI interrupt for device 000
0:02:03.0 disabled
Dec  4 20:05:58 wabbit kernel: [ 4030.480000] ipw2200: probe of 0000:02:03.0 fai
led with error -5
Dec  4 20:06:02 wabbit kernel: [ 4033.760000] input: Lid Switch as /class/input/
input9
Dec  4 20:06:02 wabbit kernel: [ 4033.760000] ACPI: Lid Switch [LID]
Dec  4 20:06:02 wabbit kernel: [ 4033.760000] input: Power Button (CM) as /class
/input/input10
Dec  4 20:06:02 wabbit kernel: [ 4033.760000] ACPI: Power Button (CM) [PBTN]
Dec  4 20:06:02 wabbit kernel: [ 4033.764000] input: Sleep Button (CM) as /class
/input/input11
Dec  4 20:06:02 wabbit kernel: [ 4033.764000] ACPI: Sleep Button (CM) [SBTN]
Dec  4 20:06:02 wabbit kernel: [ 4034.312000] agpgart: Found an AGP 2.0 complian
t device at 0000:00:00.0.
Dec  4 20:06:02 wabbit kernel: [ 4034.312000] agpgart: Putting AGP V2 device at 
0000:00:00.0 into 4x mode
Dec  4 20:06:02 wabbit kernel: [ 4034.312000] agpgart: Putting AGP V2 device at 
0000:01:00.0 into 4x mode
Dec  4 20:06:02 wabbit kernel: [ 4034.312000] [drm] Loading R200 Microcode
Dec  4 20:06:03 wabbit kernel: [ 4035.428000] ACPI: CPU0 (power states: C1[C1] C
2[C2] C3[C3] C4[C3])
Dec  4 20:06:03 wabbit kernel: [ 4035.428000] ACPI: Processor [CPU0] (supports 8
 throttling states)
Dec  4 20:06:04 wabbit kernel: [ 4035.592000] ACPI: Thermal Zone [THM] (30 C)
Dec  4 20:06:04 wabbit kernel: [ 4035.816000] ACPI: AC Adapter [AC] (off-line)
Dec  4 20:06:04 wabbit kernel: [ 4036.172000] ACPI: Battery Slot [BAT0] (battery
 present)
Dec  4 20:06:04 wabbit kernel: [ 4036.172000] ACPI: Battery Slot [BAT1] (battery
 absent)
Dec  4 20:07:07 wabbit kernel: [ 4099.224000] ieee80211: 802.11 data/management/
control stack, git-1.1.13
Dec  4 20:07:07 wabbit kernel: [ 4099.224000] ieee80211: Copyright (C) 2004-2005
 Intel Corporation <jketreno@linux.intel.com>
Dec  4 20:07:07 wabbit kernel: [ 4099.232000] ipw2200: Unknown symbol ieee80211_
wx_get_encodeext
Dec  4 20:07:07 wabbit kernel: [ 4099.232000] ipw2200: Unknown symbol ieee80211_
wx_set_encode
Dec  4 20:07:07 wabbit kernel: [ 4099.232000] ipw2200: Unknown symbol ieee80211_
wx_get_encode
Dec  4 20:07:07 wabbit kernel: [ 4099.232000] ipw2200: Unknown symbol ieee80211_
txb_free
Dec  4 20:07:07 wabbit kernel: [ 4099.232000] ipw2200: Unknown symbol ieee80211_
wx_set_encodeext
Dec  4 20:07:07 wabbit kernel: [ 4099.232000] ipw2200: Unknown symbol ieee80211_
wx_get_scan
Dec  4 20:07:07 wabbit kernel: [ 4099.232000] ipw2200: Unknown symbol escape_ess
id
Dec  4 20:07:07 wabbit kernel: [ 4099.236000] ipw2200: Unknown symbol ieee80211_
freq_to_channel
Dec  4 20:07:07 wabbit kernel: [ 4099.236000] ipw2200: Unknown symbol ieee80211_
set_geo
Dec  4 20:07:07 wabbit kernel: [ 4099.236000] ipw2200: Unknown symbol ieee80211_
rx
Dec  4 20:07:07 wabbit kernel: [ 4099.236000] ipw2200: Unknown symbol ieee80211_
channel_to_index
Dec  4 20:07:07 wabbit kernel: [ 4099.236000] ipw2200: Unknown symbol ieee80211_
rx_mgt
Dec  4 20:07:07 wabbit kernel: [ 4099.236000] ipw2200: Unknown symbol ieee80211_
get_geo
Dec  4 20:07:07 wabbit kernel: [ 4099.236000] ipw2200: Unknown symbol free_ieee8
0211
Dec  4 20:07:07 wabbit kernel: [ 4099.236000] ipw2200: Unknown symbol ieee80211_
is_valid_channel
Dec  4 20:07:07 wabbit kernel: [ 4099.236000] ipw2200: Unknown symbol alloc_ieee
80211
Dec  4 20:07:07 wabbit kernel: [ 4099.248000] ieee80211: 802.11 data/management/
control stack, git-1.1.13
Dec  4 20:07:07 wabbit kernel: [ 4099.248000] ieee80211: Copyright (C) 2004-2005
 Intel Corporation <jketreno@linux.intel.com>
Dec  4 20:07:07 wabbit kernel: [ 4099.252000] ipw2200: Intel(R) PRO/Wireless 220
0/2915 Network Driver, 1.2.0kmprq
Dec  4 20:07:07 wabbit kernel: [ 4099.252000] ipw2200: Copyright(c) 2003-2006 In
tel Corporation
Dec  4 20:07:07 wabbit kernel: [ 4099.252000] ACPI: PCI Interrupt 0000:02:03.0[A
] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Dec  4 20:07:07 wabbit kernel: [ 4099.252000] ipw2200: Detected Intel PRO/Wirele
ss 2200BG Network Connection
Dec  4 20:07:07 wabbit kernel: [ 4099.296000] ACPI: PCI interrupt for device 000
0:02:03.0 disabled
Dec  4 20:07:07 wabbit kernel: [ 4099.296000] ipw2200: probe of 0000:02:03.0 fai
led with error -5
Dec  4 20:07:29 wabbit kernel: [ 4121.464000] atkbd.c: Unknown key pressed (tran
slated set 2, code 0x88 on isa0060/serio0).
Dec  4 20:07:29 wabbit kernel: [ 4121.464000] atkbd.c: Use 'setkeycodes e008 <ke
ycode>' to make it known.
Dec  4 20:07:30 wabbit kernel: [ 4121.732000] usb 1-2: USB disconnect, address 4
Dec  4 20:07:32 wabbit kernel: [ 4123.868000] atkbd.c: Unknown key pressed (tran
slated set 2, code 0x88 on isa0060/serio0).
Dec  4 20:07:32 wabbit kernel: [ 4123.868000] atkbd.c: Use 'setkeycodes e008 <ke
ycode>' to make it known.
Dec  4 20:07:32 wabbit kernel: [ 4124.392000] usb 1-2: new full speed USB device
 using uhci_hcd and address 5
Dec  4 20:07:33 wabbit kernel: [ 4124.612000] usb 1-2: configuration #1 chosen f
rom 1 choice
Dec  4 20:08:04 wabbit kernel: [ 4156.000000] input: Broadcom Four Button Mouse 


---

### Post by svguy on 2007-12-07
Ok, tonight after work i turned the laptop off, and turned it back on at home. It beeped twice, failed to boot, and did that like 5 times before finally booting and not finding a network card.

I've restarted it almost 10 times since then and it beeps twice every boot, sometimes before bios, sometimes after, and then doesn't find the network card.

I really need help here guys.

---

### Post by svguy on 2007-12-07
Any help guys? I'm getting really desperate here and i can't find any answers on google or this forum

---

### Post by svguy on 2007-12-11
I decided to purchase another ram module and try that out as some people i know have suggested it may be ram.  I did the mem test which came back fine after 2 passes, but It does seem to fit the symptoms.
If it doesn't fix it then at least i'll have gotten a ram upgrade out of it.

---

### Post by svguy on 2007-12-14
Ok, so no one's reading this, or at least not responding. But i'm still holding out hope.

The RAM module didn't change a thing, except that it's faster now.  It still fails to boot sometimes, and still fails to recognize the network card if it beeps twice on boot.

I swapped out the hard drive for one with windows on it do flash the bios for an update, which didn't help.  But, interestingly enough, it worked fine for the hour i had windows on it.
Then i put the drive back in it with 7.10 and it immediately failed to boot with a fast flickering HD light.
It's been about 12 boots now and i still can't get it to boot while recognizing the network card.
I've already reinstalled gutsy, so now i'm thinking that there must be something physically wrong with the hard drive....yippee.

---

### Post by svguy on 2007-12-15
*sigh* the saga continues, even though no one is replying.

I got a new hard drive, and the computer worked fine for 8 or 9 boots, then this morning i went to turn it on and i'd get a power light for about 3 seconds and then it'd turn off, no bios, no nothing.  That happened about 4 times, then it booted with two beeps, and shut off.  Then i turned it on again and it works fine..
What the F

---

### Post by svguy on 2007-12-15
Talked to dell support and they said that it's either memory, or the motherboard, and since i've already replaced the memory the suggested reseating it. And if that doesn't fix it, i need a new motherboard, at $450.

The computer is the F'd and apparently will only get worse...

---

### Post by cp1969 on 2007-12-15
I can't help you one bit but thought I'd throw in my sympathy.  I'm fighting a problem of my own and I know the feeling of posting without anybody answering.

I don't know how valuable your notebook is but I'd be tempted to replace it before I'd spend $450 on a motherboard.  I bought my one of my kids a G4 Mac and the other a Toshiba.  The Toshiba was only $375.

Then you can dig the hard drive out of this one and somehow (?) get the data off of it that you need.

I totally hosed my Dell desktop in trying to get rid of a Kitro Worm, so I just bought a new hard drive, reinstalled XP and ubuntu and have the other unbootable drive as a slave to get data off of as I need it.

'Course, that solution may not be possible with a notebook.  The other option is to put it underneath the wheel of a big Dodge van and back over it, then speed off while muttering "Dang it!"

---

### Post by svguy on 2007-12-17
company i bought it from said for $70 they'll replace the motherboard and ship it back to me.  I'm outside the warranty period so it seems like a pretty good deal, and i'd rather not buy another laptop.

---

### Post by DJOMCSE2000 on 2007-12-18
All,

While I am not an Ubuntu user, I am a Dell technician for my place of employment and have seen this condition several times in the D600 laptops. The issue is with the motherboard and it will need to be replaced. I am basically a parts changer and troubleshooter in what I do regarding Dell laptops and desktops, and this is nothing new. The best way to resolve issue is to get a known-working board from Ebay or someplace like that. I have done this on several occasions. If you have any computer savvy at all, the board can be swapped out in 20 minutes if you're really good, 25 minutes if your're just good, or 30 minutes if someone is walking you through it over the phone step-by-step. It's not bad to do. I have done LOTS of these boards that have died for various reasons, including the symptoms you're speaking of.

Let me know if I can help.

- Dave -

---

### Post by svguy on 2007-12-18
thanks for the response dave. I'm glad to get confirmation that the board is toast, and for $70 i'm not scared to take that route.

Thanks

---

### Post by Riel on 2008-01-11
Here, after installing an other linux-distro, I get flashing num-lock and scroll-lock lights (d600 too). The laptop also booted slowly once. It happens every time I try to connect the WIRELESS network. 

I have a small feeling your network card fuckes a bit. Is it possible to take it out? It also doens't find it, so it makes sense. You have exactly the same network card and I happen to have some problems with it in the D600 too. (NOT on all distro's ! Try installing Linux Mint, it's ubuntu based and the only one where all my hardware workt perfect at once).

---

