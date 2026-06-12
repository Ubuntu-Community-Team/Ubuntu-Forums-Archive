---
title: "Clevo P670SE Headphone Jack Issues"
date: 2015-09-01
forum: Hardware
---

### Post by casper10 on 2015-09-01
I'm posting this because I've spent a lot of time on trying various things, and I'd like to document this searchably for others. Let me know if you need more details.

Laptop Clevo P670SE (Scan 3XS LG1720), probably on related models as well, other brands that use this barebone are Sager, PC-Specialist Optimus, Defiance, etc.
Ubuntu 15.04

Problem: Plugging in a headphone is not recognized, no sound on headphone, built-in speaker OK, and oddly enough line out is OK and even recognized.

Solution by Real Custom PC:
> sudo apt-get install alsa-tools-gui
hdajackretask

select the correct codec (by default in my laptop it selects the hdmi)
find pin 0x1b

it should say "headphone" and it probably says line out front or something

override to headphone, apply and check

if it works install boot override


This worked for me - even after restoring as much of the other files I've messed with in the process as possible.
Not sure if it matters, but I seemed to have done something wrong in my initial attempt and somehow had to do this twice. Anyway I'm really happy to have this working properly now!

---

### Post by Monkeyt on 2015-09-10
omg, thanks really thanks, it worked =D. i have a P650SG and it worked like a charm.

---

### Post by edkmho on 2015-10-27
Hi Casper10 & Monkeyt,

Are you able to get the mic working? 

I have Clevo P650SE where the headphone is working fine as per your suggestion, but unable to get the mic working. 

Please help, thanks.

---

