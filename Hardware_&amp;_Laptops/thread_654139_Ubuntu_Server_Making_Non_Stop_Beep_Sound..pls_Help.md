---
title: "Ubuntu Server Making Non Stop Beep Sound..pls Help Its Mere Urgent..."
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by gspkarteek on 2007-12-30
Hi frens of the forum,I am a system administrator newly appointed to maintain a UBUNTU Server which is used for a continous research in our university and till date every thing went well but suddenly since 2 days it is making a loud continous beep sound and i tried restarting the server and configured the drives the sound stopped and after a couple of hours it started again and the whole hard disk in the server is divided into 2 parts and both the drives are shared and when i face this beep sound problem one of the drives is completely functional and the other is not accesible.....
pls pls ..kindly tell me a possible reason and a solution for my problem...

---

### Post by gilf on 2007-12-30
Sounds like you have a failing or failed hard drive. You'll need to replace it.

---

### Post by ModelM on 2007-12-30
I've had this continuous beep happen twice. Both times it was bad RAM. If this is an MSI motherboard you might try resetting the CMOS. Some MSI MoBo's will glitch sometimes & think no RAM is installed - resetting the CMOS fixes it.

Otherwise, I'd try replacing  the RAM. I'd also strongly recommend checking the power supply. A simple tester can be had for about $15 - a friend just bought one for $12 at CompUSA. It won't check the supply under load, but a simple go/no-go power supply test is a *lot* better than knowing nothing about it.

---

### Post by gilf on 2007-12-30
I had a corporate server RAID drive down with with a continuous beep. He's got one drive not accessable.

Troubleshooting:

Open the case and find where the beep is coming from.

(In our case it was the HD controller card).

Look at the card (or MOBO ifthe beep is from there) and jot down the name and model number.

If you don't have a manual look it up on the Mfr's site on the net and download the manual

Look up the beep codes.

Identify the problem.

If they are still  in business, you can also telephone the manufacturer. This is an institutional IS emergency right?

If you are using RAID and it is a bad drive the liklihood is that one drive is handling the problem for the bad drive -- that's why you are still running with one drive inaccessible.

Good luck.

---

### Post by gspkarteek on 2008-01-03
> **gilf said:**
> I had a corporate server RAID drive down with with a continuous beep. He's got one drive not accessable.

Troubleshooting:

Open the case and find where the beep is coming from.

(In our case it was the HD controller card).

Look at the card (or MOBO ifthe beep is from there) and jot down the name and model number.

If you don't have a manual look it up on the Mfr's site on the net and download the manual

Look up the beep codes.

Identify the problem.

If they are still  in business, you can also telephone the manufacturer. This is an institutional IS emergency right?

If you are using RAID and it is a bad drive the liklihood is that one drive is handling the problem for the bad drive -- that's why you are still running with one drive inaccessible.

Good luck.
thanks a lot...

---

