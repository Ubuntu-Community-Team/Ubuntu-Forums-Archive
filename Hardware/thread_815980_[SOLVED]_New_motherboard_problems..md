---
title: "[SOLVED] New motherboard problems."
date: 2008-06-02
forum: Hardware
---

### Post by mahasmb on 2008-06-02
I just installed a new P4M900-M4 motherboard (yes, I know it's a relatively old socket 478 mobo. I didn't want to spend hundreds on a new CPU).

The computer starts on fine, LED lights work, fans work... but there's no display on the monitor. There's power to the monitor, because I can see an LED light on the monitor, but nothing shows up on it. The monitor is connected properly to the computer, and was working fine with my old motherboard.

When I start the computer, I get **two short beeps**. I'm told this can help diagnose my problem. For a different type of motherboard, it means that the RAM isn't installed properly or something. But I made sure my RAM is the proper type and installed securely.

So I really don't know what's wrong, but I've provided all the pertinent info above. Please help :(.

---

### Post by bigken on 2008-06-02
try reseeting  your ram

it could also be your onboard video

---

### Post by bigken on 2008-06-02
just another thought short your bios so it goes back to a factory default

---

### Post by Sef on 2008-06-02
> When I start the computer, I get two short beeps.

What it means depends on your BIOS. Check out [Computer beeps]("http://www.computerhope.com/beep.htm").

---

### Post by mahasmb on 2008-06-02
I made sure my RAM was installed securely and even switched memory sockets. On second thought, I can pick an extra gig of Crucial RAM for about $25. I'll try that if nothing else works.

---

### Post by bigken on 2008-06-03
have you tried one chip at a time

---

### Post by mahasmb on 2008-06-03
I only have one stick of RAM ( 1 GB).

---

### Post by bigken on 2008-06-03
do you know which bios you have so we check it against the makers code chart 

but my guess is the ram has gone bad or your video is bad do you have an old pci
or agp video card you can try on the mobo and another stick of ram any size will
do

---

### Post by mahasmb on 2008-06-03
I know I have AwardBIOS (by Phoenix, I think). My motherboard only takes 533/667 MHz DDR2 RAM. I don't have any extra ones lying around :( . Also, my motherboard comes with an onboard graphics card. I don't have an extra one of those either.

---

### Post by bigken on 2008-06-04
what are you using now ? dont you have a friend who could lend you a stick of ram to test your board with

---

### Post by mahasmb on 2008-06-04
I can get an extra 1 GB Crucial piece of RAM in a few days for like $25. I'll try that if nothing else works.

---

### Post by mahasmb on 2008-06-08
Okay, so I bought the RAM and my display works fine.

---

### Post by ricardisimo on 2008-08-09
I just bought this same board (trying to save money as well) as an upgrade over a board that wouldn't allow me to upgrade past 7.04, and so now when start up I get the Ubuntu loading progress bar graphics, and then
```
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
```
When I hit "Yes" I get
```
(EE) No devices detected
Fatal server error: No screens found
```
I tried running 8.04 off the LiveCD to see if maybe Feisty just didn't recognize the board or card, but the LiveCD desktop screen is covered in "noise" and double-images. Please see attached photo.

I will try reseating the RAM, but would love other options in the meantime.

---

### Post by ricardisimo on 2008-08-12
No luck with new RAM chips. We tried numerous combinations of three or four different chips: Two identical 512s, two different ones, just one, two identical 1Gigs... nothing. One combination did make a difference - bootup wouldn't take place at all. Other than that, they all brought me to the same error screen as before.

Any ideas?

---

### Post by Daelyn on 2008-08-13
> **ricardisimo said:**
> No luck with new RAM chips. We tried numerous combinations of three or four different chips: Two identical 512s, two different ones, just one, two identical 1Gigs... nothing. One combination did make a difference - bootup wouldn't take place at all. Other than that, they all brought me to the same error screen as before.

Any ideas?

Long shot, but, try:

* Reset the CMOS
* Unplug ALL cables from PC.
* Push in the "power button" for 30 seconds (with nothing connected!)
* Connect mains, keyb/mouse and monitor and try to power it on.

Most likley won't help against the POST beeps, but it won't harm either. We usually do this on OEM machines when getting POST issues and it actually fixes it 9 out of 10 times. It just drains capacitors and stuff and "reset" the mobo so to say.

---

