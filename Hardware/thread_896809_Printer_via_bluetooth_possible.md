---
title: "Printer via bluetooth possible?"
date: 2008-08-21
forum: Hardware
---

### Post by dewan on 2008-08-21
Hi there,

i own a nice laser printer (OKI C5300) which seems to be well supported by Linux, means up to now, i didnt have any driver related issues.

Now, i find myself hanging out with my laptop all around in different places at my home, and it is quite annoying to need to go back to the room where the printer is stored, just to connect it, print something, and then return to the place i've been before :-).

The point is, today i've found an old USB bluetooth stick i don't need anymore, and i thought, it would be great if i could have my laptop connecting to my printer via bluetooth. As my printer has an USB port, do you guys think, i could actually plug the USB bluetooth stick in it and print via bluetooth?!

I mean the bluetooth stick should 'translate' the incoming bluetooth signals into USB signals, so that the printer doesnt notice a change (am i correctly assuming that?), i think the question is whether i can convince my Hardy Heron to transmit the USB signals via bluetooth.

(As i need to buy an USB Type A to Type B adapter, so that i can plug the bluetooth stick into the printer, i wanted to make sure whether this idea is all nonsense ;) or whether i got a chance.)

Thanks for your opinions.

dewan

---

### Post by molochi on 2008-08-21
"The point is, today i've found an old USB bluetooth stick i don't need anymore, and i thought, it would be great if i could have my laptop connecting to my printer via bluetooth. As my printer has an USB port, do you guys think, i could actually plug the USB bluetooth stick in it and print via bluetooth?!

I mean the bluetooth stick should 'translate' the incoming bluetooth signals into USB signals, so that the printer doesnt notice a change (am i correctly assuming that?)"

The blutooth dongle acts as a type of network card and requires the appropriate drivers and software to be running on its host machine, ie the printer. It's unlikely that Okidata has a blutooth stack running even if it does have a decent cpu. 

What you want is a print server that plugs via USB into the printer and connects via CAT5/6 (or via wifi) into your network.

---

### Post by dewan on 2008-08-21
Awww.

A print server costs quite a bit of money, right? The good thing about the USB bluetooth dongle was, well, i already own it ;).

So no hope for the USB-bluetooth-print-anywhere idea? :(

---

### Post by molochi on 2008-08-21
I picked up an 802.11G (supporting WPA-PSK) Hawkins printserver for 50bucks at frys about a year ago. I've seen them on sale for that since then. Normal price for most wifi printservers is usually $100 +/-$20.

If you have a computer that stays on most of the time, you could just share the printer over the network from that computer. Any old system made in the last 10 years could do it. The nice thing about a printserver is it's small (about fist sized) and runs 24/7 off a 12watt wallwart. Also if it's wireless you get to put the printer where it's needed.

---

### Post by dewan on 2008-08-21
Sounds like a printserver would perfectly fit my needs :-).

I'll see if i can save some money for that, but up to than i'll stay with my USB cable :S.



Thanks for your help!

---

