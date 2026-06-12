---
title: "Ubuntu SMOKED my power supply"
date: 2008-07-05
forum: Hardware
---

### Post by FRAGaLOT on 2008-07-05
After using Ubuntu 8.02 (64bit) on my Athlon 64 x2 4800+ all day, I wanted to head to bed, so I shut it down, but something went wrong. I saw my PC POST again and freeze.  I thought maybe I clicked on restart button, not the shutdown button. But it froze on the BIOS splash screen, and then I could smell burnt electronics coming from my PC!  OH NO!!!!!!

After verifying that the smell was coming from the power supply, I swapped it out for another one I had in a different computer I wasn't using. It worked fine, but when I went to shut it down, it DID NOT power off my system completely. All fans were still spinning, the on board lights were flickering (AN8 Ultra has a lot of red LEDs all over it) and my speakers were making clicking noises.  Something isn't right, and something in Ubuntu isn't properly shutting down my PC.

In all my years building, troubleshooting, and using PCs (even before BTX systems came around) I've never seen an OS have a problem turning off a computer, let alone FRY a power supply. Yes I'm rather ticked off that something so HYPED as linux/ubuntu is so wonderful that it would destroy hardware. I would have though windows would be the first to that.:lolflag:

Anyhow this is my rig, maybe someone knows if Ubuntu just doesn't like my hardware configuration:
AMD Athlon 64 X2 4800+ (slightly OCed to 2.5ghz)
Abit AN8 Ultra
GeForce 6800 GS w/ 256m
WD 400gb SATA HDD
2GB RAM
Standard DVD burner drive
Onboard sound

I also have an APC UPS power backup that does a really good job at cleaning my crappy power from PG&E that likes to drop voltages every now and then (especially now in the hot summer weather when we need to run the air conditioner). So I know my power is decent with the UPS in use.

The PSU I originally had that burned out was a RAIDMAX model RD-350W. The PSU I have in this PC now is an Antec SL300S (300w model) which still has problems shutting down, but at least it's not smoking up.

Another thing I should point out that I've only had Ubuntu installed for about 3-4 days now. The day this happened (July 4th) there were some automatic updates to Ubuntu that were downloaded and installed, but I have no clue if this was the cause of my PSU problems, since there were dozens of them. However the day before these updates were installed I wasn't having these problems.  But I do believe that Ubuntu is to blame for my blown PSU.

This is also the first time I used the 64bit version of ubuntu, but I'm finding it to be as slow (maybe slower) than the 32bit version I had been running on an Athlon XP 3000+ rig (that's the PC I've been running the 32bit Ubuntu on).. and if it's blowing up PSUs like this I REALLY don't think I'll be using this much longer.

__FRAGaLOT

BTW, I'll remove the overclocking back to stock speeds, and see if that is related.  But I highly doubt it.. never had problems with windows XP for the years I had it like this... but it would be unwise not to rule this out.

---

### Post by bigken on 2008-07-05
you mobo could have a fault i very much doubt its anything to do with ubuntu

---

### Post by FRAGaLOT on 2008-07-05
Actually I think it's the PSUs I'm using are just way underpowered.

After changing bios so the CPU is back to stock speeds, I powered off the PC manually before the OS loaded in, and it did the SAME weird clicking and flashing LEDs on the mobo. The clicking/flashing eventually petters out till it drains power, but it's got to be bad for the mobo. So, the blame isn't on ubuntu, but why didn't it do this yesterday? I don't think the blame is on my motherboard either.

Both PSUs are 300w dealios I've had for a long time. One of them is probably just old and it just gave up the ghost finally. The other one, an Antec PSU (which are of decent quality) probably just isn't fully compatible with my mobo.  Considering what power is needed for this hardware, a 300w PSU just may not be good enough for it. Plus it has a 20 pin connector when the mobo has a 24pin connector.  But this is all I got for now.

---

### Post by gilbertr on 2008-07-05
You're right.

Your PSU just isn't up to it.
300W for this system is not enough and using 20-pin on a 24-pin MB is never a good idea.
Based on the hardware you listed, I calculate your requirements around 400W.

Running on low power isn't ideal for any device in your PC, not just for your MB, I'd actually be more concerned for your HD.

---

