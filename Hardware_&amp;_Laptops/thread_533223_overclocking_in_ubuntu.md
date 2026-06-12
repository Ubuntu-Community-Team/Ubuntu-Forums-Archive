---
title: "overclocking in ubuntu"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by jacob01 on 2007-08-23
has any one successfully overclocked any hardware (cpu video card ram) running ubuntu through software

---

### Post by ubuntu.daemon on 2007-08-23
not that i know of, but are im assuming you're talking about linux-native programs.... doesn't you're bios have these options?

---

### Post by EXCiD3 on 2007-08-23
nvclock is a program for overclocking your nvidia video cards.

---

### Post by dabl on 2007-08-23
I kept a small Win XP partition just to run the Intel overclocking utility for my motherboard. I have it overclocked to 3.3GHz (stock is 2.93). That's actually the only remaining reason that I need a native Win XP installation.

On my Nvidia card, if you use the proprietary driver and include the "Coolbits" option in xorg.conf, you can overclock the card for the session. But it resets after a reboot, so you have to set it every time you want to overclock it.

:guitar:

---

### Post by jacob01 on 2007-08-24
> **EXCiD3 said:**
> nvclock is a program for overclocking your nvidia video cards.

is there a linux native nvclock

---

### Post by Steveway on 2007-08-24
nvclock is a native linux-app.
There are even several frontends.
nvclock-gtk or nvclock-qt...
Look into Synaptic.
But keep in mind that Overclocking is a pretty useless thing, "Look my CPU runs 20MHZ faster, I need a big *** fan but it's faster!"

---

### Post by jacob01 on 2007-08-28
> **ubuntu.daemon said:**
> not that i know of, but are im assuming you're talking about linux-native programs.... doesn't you're bios have these options?

no of corse not its a dell bios

---

### Post by jacob01 on 2007-08-28
> **Steveway said:**
> nvclock is a native linux-app.
There are even several frontends.
nvclock-gtk or nvclock-qt...
Look into Synaptic.
But keep in mind that Overclocking is a pretty useless thing, "Look my CPU runs 20MHZ faster, I need a big *** fan but it's faster!"

it adds up, did you run a game or record fps or anything to see any difference?

---

### Post by ragrim on 2007-08-28
> **Steveway said:**
> nvclock is a native linux-app.
But keep in mind that Overclocking is a pretty useless thing, "Look my CPU runs 20MHZ faster, I need a big *** fan but it's faster!"

Have you any proof to the overclocking is usless claim?

im running an E6300 Core 2 duo which is stock speed of 1.83ghz i overclock it to 3.2ghz on stock cooling and when i do that it increases my Multimedia converting speed by up to 30% and it gives me an extra 10-15% in score on 3DMark benchmarks.

Maybe you should try it before you claim its useless next time :)

---

### Post by jacob01 on 2007-08-31
yea iv heard that over clocking video cards can increase their performance alot

just because you didn't notice any performance change in what ever you do doesn't mean over clocking doesn't increase performance you could have had a card that didn't over clock well
and if over clocking isn't anything special then why do so many people do it?

---

### Post by jacob01 on 2007-08-31
> **ragrim said:**
> Have you any proof to the overclocking is usless claim?

im running an E6300 Core 2 duo which is stock speed of 1.83ghz i overclock it to 3.2ghz on stock cooling and when i do that it increases my Multimedia converting speed by up to 30% and it gives me an extra 10-15% in score on 3DMark benchmarks.

Maybe you should try it before you claim its useless next time :)

3.2 per clock?

or is that both cores combined

---

### Post by PriceChild on 2007-08-31
I would strongly warn anyone against over clocking.

Hardware is only rated to a certain point. If you force it past that, you will most probably lose stability and could cause hardware failure.

---

### Post by glotz on 2007-08-31
On the other hand you can extend the life of hardware you'd end up chucking otherways. I oc'd my old Riva TNT2 card with the mentioned nvclock with good results to be able to get higher FPS rates in Wolfenstein: Enemy Territory. Sure worked nice.

I think the biggest problem with oc'ing is with providing sufficient cooling. Don't funk with hardware you can't afford to lose and go gradually and know when to stop.

Also, I don't think there's point in discussion oc'ing in general here. The internet is full of pro and con discussions.

---

