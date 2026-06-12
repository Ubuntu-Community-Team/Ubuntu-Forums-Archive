---
title: "New build want to double check if parts will work with ubuntu"
date: 2015-01-20
forum: Hardware
---

### Post by charles45 on 2015-01-20
So I'm a little younger then most people in the pc world and on a tight budget so I was wondering if anyone happens to know if these parts (below :P ) are compatible I went through like 30 pages on the compatible hardware thread and couldn't really find anything. Thanks

Intel pentium g3258
Amd HD 4850 (Yes I know this will be a pain but I got it for $20)
8 Gb generic 1600mhz ram (single channel)
Cheap biostar mobo w/ B85 chipset and dual realtek 10/100/1000 NICs
320Gb western digital 5400rpm 2.5" HDD (raiding the laptop, sorry for the awful pun)
500w coolmax 80+ certified psu (have it laying around)

If you happen to know any of this works with Ubuntu please let me know! Thanks again.

I hope I don't have to use stupid windows....

---

### Post by tokyobadger on 2015-01-20
Which specific model of the biostar B85 is that? I just looked and they have 11 variants on their webpage - clicking a couple of models I see some support your specific CPU and some don't have it listed (you've probably already done this homework).

Other than that you've correctly identified that the GPU could be a challenge - not an AMD/Radeon user but IIRC if you want fglrx you'll need the legacy driver. The 5400rpm HDD is also not going to add to the experience but I understand that you're making the most of what you've got (this box was built in early 2009 and the one beside it in 2006) - just to point out that full-fat Ubuntu with that GPU/HDD combo may not give the best impression, but definitely try it.

The PSU will give you headroom to upgrade, should be more than enough for the rest of the hardware.

It's definitely important to research linux compatibility, but I'd also say that it's equally important to ensure compatibility amongst your components irrespective of OS. If it works together then it should work with linux (at least the non-latest stuff).

Good luck

---

### Post by charles45 on 2015-01-20
[FONT=helvetica][COLOR=#4d4d4d]Hi-Fi B85N 3D v5.2
[/COLOR][/FONT][FONT=helvetica][COLOR=#4d4d4d]That's the mobo model from biostar. I know that it may not be the best machine ever but it would probably be a guest type pc, because me and my friends play minecraft, but they all have laptops. Currently my main computer is a windows 8.1 machine with an A10-5800k (in dual graphics mode), An HD 4850 (until april), and a 128gb ssd. So it won't be my first build, just my first linux build . In April however I will replacing the HD 4850 with a GTX 970 for my birthday.[/COLOR][/FONT]

[FONT=helvetica][COLOR=#4d4d4d]The Amd HD 4850 was too hard to get going on windows, but it also wasn't a walk in the park, I had to find the correct drivers (the legacy ones) which when I installed them without knowing they uninstalled the apu drivers. Then after that was fixed I had to do a registry edit.
[/COLOR][/FONT]

---

### Post by tokyobadger on 2015-01-20
As expected you already did the homework on CPU & mobo. That GTX970 sounds nice :-)

Good luck on the build and the install - have fun

---

### Post by charles45 on 2015-01-20
Yeah it sounds really nice just have to get some games to play on it other than minecraft xD. Thanks

---

### Post by oldfred on 2015-01-20
I just built new system Asus z97-AR and tried to use my older power supply. It was a standard ATX, but 4 or 5 years old.
Motherboard gave nothing but errors. Went back to Microcenter and paid the $10 to prove rest of system was ok and it immediately worked. New power supply and no issues. (Well lots of configuration to get it to work in UEFI mode).
Or if system has issues suspect power supply.

---

### Post by Yellow Pasque on 2015-01-20
> **tokyobadger said:**
> if you want fglrx you'll need the legacy driver.

fglrx/Catalyst Legacy only works with older (<= 3.2) Linux kernels, and subsequently with older versions of Ubuntu <= 12.04.1. You should probably not even mention it because you're just going to confuse n00bs.

The open source radeon driver will work fine for a RadeonHD 4000 card.

---

### Post by charles45 on 2015-01-20
The psu I have is less then a year old, I just wanted a better one for when I get the gtx970 for my main pc (where the 500w came from)

---

