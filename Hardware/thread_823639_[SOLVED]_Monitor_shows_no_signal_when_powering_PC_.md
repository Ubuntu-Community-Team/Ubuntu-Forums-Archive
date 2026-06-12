---
title: "[SOLVED] Monitor shows no signal when powering PC up"
date: 2008-06-09
forum: Hardware
---

### Post by Cha0tik on 2008-06-09
Hi all,

My computer had been runnning file for months. I have a P4 3.2Ghz Prescott CPU with 2gb RAM (2x 1gb) on an Asus P4C800 Deluxe mobo and an Nvidia XFX video card.

I reinstall Ubuntu last night only to find out I had to change the way my HDDs were plugged in so that the HDD where Ubuntu was installed could be made the Primary HDD in the BIOS so that it could be booted on.

I don't what happened but ever since I did this, when I power up the PC, everything starts up just fine but I get no signal on the monitor.

Here's what I tried to troubleshoot the issue:
1- Removed all memory -> Mobo doesn't warn me with a beep
2- Put the XFX in my wife's PC -> it works in that one.
3- Unplugged absolutely everything except on HDD -> no luck
4- Put in my wife's vid card (ATI Radeon 9700) that works for her -> Still no signal
5- Swapped my monitor with hers -> using her monitor, doesn't work either.
6- Took the no name 400w PSU out and replaced it with a Cooler Master 500W I had hanging around which is supposed to be of much higher quality -> Nope.. still doesn't work
7- Used different power cords to power up the video card in case powering it up was an issue -> The fan on the card turns fine in all cases but I never got a signal either.

It looks like I've narrowed it down to the mobo...
Is my method good? Anything else I should try? I don't want to buy a new mobo just to find out it still doesn't fix the problem. Not to mention that Socket 478 mobos are not as available anymore so I may have to settle for a lesser one than my Asus P4C800 Deluxe.

I know it's not directly Ubuntu related but I find the level of technical knowledge on this forum far exceeds other forums out there.

Thanks guys !

Cha0tik

---

### Post by wdaniels on 2008-06-09
Do you even get the initial BIOS loading screen or is there no signal at any point at all?

---

### Post by Cha0tik on 2008-06-09
I can't see the BIOS.
I don't get a signal at all.

---

### Post by wdaniels on 2008-06-09
I've only heard of this twice; once the problem was with the memory and the other time had something to do with the actual mains power supply. I know it's a long shot, but have you tried plugging the monitor into a different mains outlet? Do you have any other RAM chips to try?

Wish I could be of more help, but I don't know what else to suggest :(

---

### Post by Cha0tik on 2008-06-09
Tonight I will pick up new RAM at the store and see if it fix this or not.

If it doesn't I can always exchange the RAM for a mobo or a PSU and try those things as well.

I'll update this thread and I find out more info.

Thanks !

---

### Post by Cha0tik on 2008-06-17
For everyone's information, it turns out that the hardware was fine.
In order to fix this, I had to reset the CMOS on the motherboard and that fixed it right away.

---

### Post by ukripper on 2008-06-17
> **Cha0tik said:**
> For everyone's information, it turns out that the hardware was fine.
In order to fix this, I had to reset the CMOS on the motherboard and that fixed it right away.

I thought so  BIOS is here the culprit, but great you fixed it before i could post :)

---

