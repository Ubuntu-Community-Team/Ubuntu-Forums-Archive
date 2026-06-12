---
title: "P45 mobo - network and sound?"
date: 2008-11-11
forum: Hardware
---

### Post by SeePU on 2008-11-11
I'm looking at P45 motherboards but I'm not finding much info about sound and network compatibility.  I have found some posts but I'm not sure if they are still relevant as there might be updates by now.

I'm hoping owners of P45 boards could reply and give feedback and confirmation of what works (or doesn't).

I'd be using Ubuntu or Kubuntu 8.10 Intrepid Ibex.  

Here's the hardware that I'm looking at:

Network (LAN chips):
Realtek 8111C (in many P45 Gigabyte boards)
Marvell 88E8056/88E8001 (in many P45 Asus boards e.g. P5Q-E)
The Marvel one is dual LAN so there's the option of two choices?

Sound (audio chip):
Realtek ALC889A codec (in P45 Gigabyte boards)
ADI AD2000B codec (in Asus P45 boards e.g. P5Q-E)

Many of these boards only have 2 PCI slots so LAN and/or audio issues would require filling up one or both slots with a NIC and/or a sound card.  I might get a Creative X-Fi sound card but it would be convenient and open a PCI slot if I could use the onboard LAN.

Anyone know which one works (for sure)?

Thanks in advance for any answers.

---

### Post by szale9001 on 2008-11-13
I also have this exact same question regarding much of the same hardware. I don't want to get a mobo that will be a nuisance to get operational.

---

### Post by null_pointer_us on 2008-11-13
> **SeePU said:**
> I'm looking at P45 motherboards but I'm not finding much info about sound and network compatibility.  I have found some posts but I'm not sure if they are still relevant as there might be updates by now.

...

Here's the hardware that I'm looking at:

Network (LAN chips):
Realtek 8111C (in many P45 Gigabyte boards)
Marvell 88E8056/88E8001 (in many P45 Asus boards e.g. P5Q-E)
The Marvel one is dual LAN so there's the option of two choices?

Sound (audio chip):
Realtek ALC889A codec (in P45 Gigabyte boards)
ADI AD2000B codec (in Asus P45 boards e.g. P5Q-E)

...

Anyone know which one works (for sure)?

I have a P35-based board with Realtek ALC888 (sound) and Marvell 88E8056 (network). They've worked OOB (out-of-the-box) with Fedora, Ubuntu, etc. The only setting I had to change was the volume. :)

The only problem I had with the ALC888 was a minor suspend issue (module: snd-hda-intel) where I would lose sound after the PC awoke from sleep mode, but that has been fixed in Ubuntu 8.10.

IMO the P45 boards should work fine.

If you do not get any specific confirmations here, there's always Google and the forum search, which might be used to locate success stories for specific motherboard models you are considering.

---

### Post by szale9001 on 2008-11-13
Thanks for the reply. I have done come googling myself. The results were a little less than inspiring. See, I read of a few problems regarding that Marvell LAN chipset and Ubuntu 8.10. Can anyone with a P5Q-E or variant with a Marvell LAN chipset confirm that there has been no problem recently with Intrepid? I mean its possible it has been fixed already in Intrepid but I havent seen it yet.

---

### Post by SeePU on 2008-11-14
Szale, that's what I found, too.  The other poster should know that I *DID* Google and search for the answers.  Like you, I found people *claim* problems or issues but these might have been solved by now.  The reports of problems were a while ago and the kernel/network issues keep getting updated.  Whether this has solved any of the issues is an unknown at this point, I think.

Some of the dual LAN boards may have one port that works and one that doesn't , for e.g.  I think that the P45 Asus boards might have at least one LAN port that works ('not sure if the other one will but there are posts of it not working without a lot of tweaking).  I don't know about the Gigabyte boards with the (Realtek) RTL8111C LAN chips.  The RTL8111B works for sure but those are mostly in P35 boards.  The other question is whether they work OOTB (out of the box) which is what I want to know/confirm.

---

