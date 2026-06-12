---
title: "Ubuntu Hangs when I try to change my Wireless"
date: 2005-11-23
forum: General Help
---

### Post by rold50 on 2005-11-23
Hi,

When I go to networking and try to change the essid from the drop down list for the wireless... after I 'ok' it. 50% of the time my Ubuntu hangs.



Any Idea why this happens?

---

### Post by 23meg on 2005-11-23
What's the brand and model of your wireless device?

---

### Post by rold50 on 2005-11-23
it's a broadcom. it came with my gateway laptop.

I'm using ndiswrapper.

It works fine when I eventually is able to change the essid.
It's just that I use my laptop in school and at home. They have different networks.. so I have to change it each time I go to school and back home.

It's just that the hanging part is annoying. add to that my start up is taking really long in the configuring network device.. part..

---

### Post by 23meg on 2005-11-23
Try using GTKWifi to do the network switching and see if it helps.

---

### Post by Eversmann on 2005-12-08
I have the same problem with my Asus Z92U laptop using Broadcom drivers installed with ndiswrapper.

Randomnly, it hangs when i use the wireless (only with wireless). It is just like the mate said, 50% of the time.

Anyone could give us some light on this? maybe it's a ndiswrapper problem. I'm using 1.14 (taken from the ubuntu repository).

In windows it works perfectly, no problem at all (but i want to get rid of windows :-D )

thanks guys.

---

### Post by rold50 on 2005-12-08
I installed GTKWifi and I haven't had a hang-up ever since. =)

---

### Post by brallan on 2006-04-23
[QUOTE=Eversmann]I have the same problem with my Asus Z92U laptop using Broadcom drivers installed with ndiswrapper.

Randomnly, it hangs when i use the wireless (only with wireless). It is just like the mate said, 50% of the time.[/QUOTE]

Yeah, I am having the same problem, also with an [ASUS Z92U]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusZ92U") with breezy and ndiswrapper at bootup, but once I get it working it works like a charm. Here's what I do, (though i'm embarrased to admit it): After bootup I go into System>administration>Networking and deactivate my network connection, then choose Wireless connection>properties and reselect the router, OK then reactivate the wireless connection, which in breezy is wlan0. The strange thing is, the light does not come on for the wireless card even when it's working, but I gave up on pressing <Fn><F2> as it didn't work, merely froze up the whole system. perhaps i could run some kind of script at bootup to  do a modprobe ndiswrapper or something like that but I don't know how.

Dapper seems to detect it as eth0 and the ethernet card as eth1, but I gave up on the dapper install before I could find out if the new broadcom drivers are in dapper and would work or if I would need to use ndiswrapper again.

---

