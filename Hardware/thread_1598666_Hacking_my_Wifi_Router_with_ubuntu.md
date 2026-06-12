---
title: "Hacking my Wifi Router with ubuntu"
date: 2010-10-16
forum: Hardware
---

### Post by zzzakattack on 2010-10-16
Right now, I'm working on a project with a really old computer, that unfortunately can only use wireless networks and can only use WEP and not WPA encryption (which is what my network is on), plus it can't use Ad-Hoc networks, only access points.

Luckily, I have a spare wifi router laying around that isn't doing anything.  I know that if I set my Ubuntu laptop to connect to my WPA router, I can share that network via an Ethernet cord to another computer.

I figure that if I do this, then hack an ethernet cord and a modem cable, by cutting each of them in half, then rewiring them to each other, I could hook my laptop to my WPA wifi, then share it by putting the ethernet end of my cord into my laptop, and hooking the modem cable part into my router, my router might be able to get to the internet, and spread it's wifi.

I'm sure everything will work except the part about hacking my ethernet/modem cable to become one cord.  Is this idea plausable? or maybe even possible?  Thanks in advance!

---

### Post by TBABill on 2010-10-16
Are you talking about a telephone cord (flat 4-wire cord) as a "modem cable" or a coaxial cable like for cable television (cable modem)?

Regardless, ethernet is a specific communication technology that is in no way similar to either telephone or cable. It is 8-wire for a reason and there are specific standards for twists per inch (each pair of wires - blue, orange, green and brown - is twisted at exact numbers of twists per inch). You cannot simply splice ethernet wires to another type of cable and expect the output to be recognized by any device. 

Standards for ethernet wiring:
[http://en.wikipedia.org/wiki/Category_5_cable#Conductors_required](http://en.wikipedia.org/wiki/Category_5_cable#Conductors_required)

Can't you take the output of one port from your WPA enabled router and plug it as an input to the WEP enabled router? That way your Ubuntu computer would remain on the WPA one and your other would connect to the WEP router, which is hard wired (via ethernet) to the WPA router. I'm not sure that's possible...have never actually tried...but is more along the lines of your ultimate goal. Splicing together two different cables for a useful output will not work.

---

### Post by zzzakattack on 2010-10-16
Thanks for your reply, it's helpful since I'm not to much of a hardware person, and don't know this stuff by heart.  And sorry for not making it clear, but I meant the telephone cord when I said Modem Cable.

I don't think it would be possible to connect my WPA router to the What-Would-Be-WEP router, because they only take one input of where they get their internet from, which is the telephone cable, and they only give it out through Ethernet, USB, or WiFi, so either way, the two routers couldn't share with each other, unless it was through Ethernet, which was why I wanted to hack the cords.

Haha, I am however a software person, and know that either way, my Ubuntu would be connected to the WPA.

For anyone else reading this, I do know that there is a way to make your Ubuntu an Access Point instead of an Ad-Hoc network, but was trying to avoid it through this cord hacking method.  It has to do with sharing the Ethernet through your WiFi card like an Ad-Hoc, except with different settings that only some WiFi cards can use.  I haven't done this yet, but it's supposedly complex and the instructions vary from user to user...sounds like a challenge I'm up for! :)

Thanks for you help.
Zak

---

