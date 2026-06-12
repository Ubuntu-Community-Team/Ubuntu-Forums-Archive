---
title: "Severe lockups ..."
date: 2010-03-30
forum: Hardware
---

### Post by lexe-cc on 2010-03-30
Hi,

first of all I want you guys to know I've been googling the internet for 3 months now. This is the point where I'm completely out of ideas :)

Recently (3 months ago) I bought a new computer. I ordered the following hardware:
- Intel i7 920 cpu (@2.6ghz)
- Corsair 6gb RAM @ 1333mhz
- Asus P6T SE motherboard
- Corsair 550W PSU
- MSI Nvidia GTX260 GPU
- standard dvd rom, hdd and case

Let's put it this way, this rig never worked properly. I've been having random lockups. These lockups leave random traces in the error logs or none at all. This happens in both ubuntu linux and windows 7 ultimate.
These lockups begin with non continuous stuttering of image/mouse/audio. The stuttering gets worse if I don't reboot until the point the computer locks up entirely and give me no other way out than the hardware reset button.

Untill today I've been searching for the cause of these problems. First I thought these were software problems but because it happens in ubuntu AND windows I've soon become to understand it's the hardware.
The only thing is that I really don't have a clue of which hardware component is malfunctioning.

I tried numerous times of reinstalling my operating systems. Tried different distro's of ubuntu, tried updating the drivers, updated the BIOS to the latest version, ran memtest86 for 2 straight hours (got through the first pass without any errors), ... all to no avail.

I've replaced the original PSU with a Antec 750W and replaced the harddrive. This also didn't help. My friend bought the same setup right after me, and his setup works correctly, so tomorrow I'm swapping memory modules. 

I've emailed the hardware store to inform them I'm having hardware problems and I'm thinking it's the motherboard. They said I could sent it in, but obviously I'm not willing to pay transporting cost for this if it turns out no crashes occur while they're testing because they're so damn random.

Does anybody have any clue of what's going on here or does anyone has experience whatsoever about random lockups? As far as I'm concerned it can be the motherboard, CPU, RAM, or GPU. Could you guys give me typical symptoms of any of these 4 possible malfunctioning components?
Any information that can shed some light on this would be greatly appreciated ..

Thanks in advance,
Lexe

---

### Post by IcarusR on 2010-03-30
If this happens under windows & ubuntu it is not an OS problem.

First I would check the BIOS settings are correct, or set to default.
I would suggest trying a different graphics card.
Try with 1 ram stick at a time.

Do all the above separately & run system to check for lockups each time.
Only do one thing at a time.

> ran memtest86 for 2 straight hours (got through the first pass without any errors)

To me this sounds very quick for 6Gb ram. I would let it run overnight. 

Do you have any other hardware in the box, pci cards etc ? Remove all except necessary stuff & try it.

---

### Post by lexe-cc on 2010-03-30
First of all, thanks for your quick reply

I'm swapping memory modules tomorrow with a friend of mine, so I'll skip memtest etc ..
The BIOS settings are all at default. So I guess this should work.
Too bad I don't have a spare graphics card too use, so I guess I can't do this test.

According to your reply may I assume you don't think it's the motherboard itself? Nor the CPU? Because these are my main concerns you see :)

---

### Post by IcarusR on 2010-03-30
My suggestions were for elimination purposes. These can be done relatively easily with no cost.
If it still locks up having done all my suggestions I would guess it to be a faulty mobo.
In my opinion unlikely to be CPU, they tend to work or not at all, in my experience.

You could try your friends graphics card as well.

You could also try removing & re-seating all memory modules & graphics card.

---

