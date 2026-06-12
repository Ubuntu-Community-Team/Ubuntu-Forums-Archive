---
title: "Boost wifi-antenna power?"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by steffennielsen on 2006-04-08
Hi There,

I have just bought a 5 dBi antenna, and want to use it fully!

Can I somehow boost the power on the antenna? (though not recommended by the manufacturers)

---

### Post by ksudbury on 2006-04-08
Wat do you mean ? You have a 5dbi antenna and wish to use it fully ?? Have you connected the  antenna to the card ? Also, wat card do you have and wat antenna ? How are you wanting to boost it? omni or yagi ? 

Keith

---

### Post by futz on 2006-04-08
[http://www.freeantennas.com/](http://www.freeantennas.com/)

Have a look at the links here. If you build one and it doesn't work, at least you're not out any money and very little time.

---

### Post by steffennielsen on 2006-04-17
[QUOTE=futz][http://www.freeantennas.com/](http://www.freeantennas.com/)

Have a look at the links here. If you build one and it doesn't work, at least you're not out any money and very little time.[/QUOTE]

Nice page!!!

But I was thinking about a software-solution

sudo iwconfig eth1 txpower 30mW

...But my card does not support that!

---

### Post by steffennielsen on 2006-04-17
It's a "RaLink RT2500" if that helps anything!

This is the antenna:

[http://www.nedis.com/Articles/Sweex/CMPS-NA001.php](http://www.nedis.com/Articles/Sweex/CMPS-NA001.php)

---

### Post by polo_step on 2006-04-18
[FONT="Courier New"]That's an aftermarket omnidirectional antenna.

My experience with them hasn't been gratifying.  I've seen no measurable improvement in the signal over the packaged external antennas that come with most decent cards...though they may help if the card comes with a screw-in antenna attached the PCI mounting bracket.

As far as a software solution to improved signal strength for this card, I know of nothing, and I've looked about a bit.  I've never been able to get wireless to work adequately for my needs in Linux at all, come to that, so I'm still wirelessing (is that a word?) in XP. 

The best thing to do with an omni is to give them a reflective backstop of some sort that will give them a directional boost.  By simply putting the base antenna in front of a flat metal surface perpendicular to the direct line to the remote antenna, I've managed as much as a 7dBi boost by actual measurement, given a little fiddling with the distance between the antenna and the metal surface.

Good luck!

[/FONT]

---

