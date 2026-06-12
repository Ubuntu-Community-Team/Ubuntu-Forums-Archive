---
title: "Avermedia DVB-T 761 card."
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by andyp11 on 2006-04-30
Has anyone managed to get this tv card working in Ubuntu? Or know how to? Or know a man who might? Or anything?

---

### Post by jdpipe on 2006-11-12
> **andyp11 said:**
> Has anyone managed to get this tv card working in Ubuntu? Or know how to? Or know a man who might? Or anything?

I've had a little look at this as as far as I can tell, Ubuntu finds the card but doesn't find the *tuner* for this card. Looks like you may need to download source firmware for 'hotplug' -- whatever that means -- and my also need to set some kernel module settings for the Spase sp887x card that I believe this video card uses for its tuner.

Have tried quite a bit to get this to work under linux (FC3, FC4, Ubuntu 5.10, 6.06) with no luck. I would recommend throwing out the card and buying one that is known to work easily.

---

### Post by andyp11 on 2007-01-01
Just noticed this response from a while back. Actually it's working fine now and has in breezy, dapper and edgy.

If anyone's interested what I had to do was

copy firmware file dvb-fe-sp887 (easily found by googling) to /lib/firmware/kernal/
(if you update the kernal then this'll need recopying)

Then
sudo modprobe bttv
sudo modprobe dvb-core
sudo modprobe dvb-bt8xx
sudo modprobe sp887x

or load them on boot

Then use Kaffeine to watch from the DVB bit, obviously initially you need to channel scan from whatever transmitter you use.

Thanks for the response

---

