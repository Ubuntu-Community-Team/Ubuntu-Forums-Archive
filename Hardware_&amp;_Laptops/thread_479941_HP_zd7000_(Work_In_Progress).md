---
title: "HP zd7000 (Work In Progress)"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by HarshReality on 2007-06-20
OK, so I have a zd7010us and a long long time ago ina galazy far far away I ran Slack (v10) I had issues with the card reader etc. etc. but I found a guide that pretty much gave me all the ins and outs and it was really nice... then came Vista and out of curiosity I killed slack and put Vista on it. Today (well actually for some time now) I hear about the Fawn so here I go again and low and behold some of the gear does not work (despite "yea it should due to kernel advancements" **not ness Ubuntu related) so here is what I am going to be doing... I'll of course post a log here as/if I get everything going and if anybody else has luck they can of course chime in...

Noteworthy mentioning I have changed out the deault CDRW/DVD in favor of a DL DVDRW and I just didnt like the whole ndiswrapper broadcom game so I hacked the BIOS to get at the white list so the system would accept a Intel 2915 a/b/g wireless card. Aside of that and the memory upgrade though she is stock.

If there are any other kids out there who would like to play the URL to the slack tutorial I originally used is here: [Tutorial]("http://home.satx.rr.com/thegood/linux-pages/linux.html"). It has ALOT of information and even a custom kernel config (for an older kernel but hey... vanilla might be the way to go.

But as I say, chime in... especially if you get the card reader going (yes I searched here and the results are less than promising)
[I]02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
	Subsystem: Hewlett-Packard Company: Unknown device 006a
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at d2006000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 50000000-51fff000 (prefetchable)
	Memory window 1: 54000000-55fff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001
[/I]

---

### Post by HarshReality on 2007-08-29
Everything works but for the card reader and the IR as far as I can tell. In the area of the wireless I chose an alternative to broadcom. I decided as the Intel 2915 DOES work out of the box to try it. The problem was HPs BIOS is whitelist guarded, simply put if your not on the "A" list in BIOS the system will halt. Using a general tutorial I found here:
[http://www.richud.com/HP-Pavilion-104-Bios-Fix/](http://www.richud.com/HP-Pavilion-104-Bios-Fix/)

I edited my stock F.35 BIOS and removed the broadcomm adapter and added my Intel (got off eBay for 12.00 shipped) and flashed it. Ironically when I rebooted with the broadcomm adapter in I got the "104 unsupported hardware" and halted. When I removed it however and put my Intel in TADA!!! so I went from G support to A,B, & G. While I realise this may be more of an in depth option that most would like I'm simply pointing that it is an option.

At this time I'll say I have both my zd7010us F.35 supporting the intel 2915 as well as the CTO zd7000 F.35 modified both tested on my system and validated. Be advised as with any sort of "mod" like this there is always a hazard and danger of DOA the board... its unlikely since all I did was modify my whitelist but still possible and to do so would be at your own peril.

I would suggest before doing the flash of your altered firmware that you download the stock from HPs site just in case. AND once you flash and validate it boots without the error just for grins reboot and try and enter BIOS... you'll find that if you try the old "change the startup logo" alteration that you wont be able to get into change your BIOS settings ;)

---

### Post by HarshReality on 2008-05-26
OK, so I let this one go for a long time (yea I put XP back on) but.. my kid has an OLPC and Im putting Xubuntu on it and for thier direction I need another linux PC.. I could use a live CD and be done but why not lets see if I can make the card reader work this time.

So, I come across a post on another distro forum pertaining to my ENE CB-710 problem and according to what they say...

Quote:
I switched off the HT SMP (It's not much performance difference, linux can multitask as well as the CPU can, it seems) and things seemed to clear up. Works every time now. I tried this earlier, but I don't know what I got right. I went into pcmcia.opts and dropped in what lspci -v told me and made sure I had all the hotplug stuff selected in the kernel. It just seems like yenta gets a bit cranky under SMP?

Now if I can figure out how to turn HT and SMP off (Im pretty sure it will involve another kernel compile) then I will test this one out.

Comments and suggestions are welcome as always.

---

