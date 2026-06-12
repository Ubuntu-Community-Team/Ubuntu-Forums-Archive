---
title: "Acer Aspire 5810TZ-4274 Wifi doesn.t work- Ubuntu 9.10"
date: 2009-12-28
forum: Hardware
---

### Post by Jabrouwer on 2009-12-28
Firstly, I am a noob ubuntu user. I recently updated from 9.04 (in which, I had no problems) to 9.10, and the wifi connection on my Acer Aspire 5810TZ-4274 no longer works correctly.  It connects to networks (I have only connected to networks with WPA or WPA2 Personal passwords) but after about 20 - 30 minutes of use, it loses connection and will almost never reconnect by itself.  The only ways I have found to reconnect is to: reboot, suspend my session and then re-enter, or tell the network manager to disconnect then reselect a network to connect to.  These usually only work for 10 - 20 minutes, then the problem re-establishes itself.

I would like a permanent solution, can anyone help?

---

### Post by grantbow on 2009-12-28
I have a 4810TZ-4696 that had an Atheros problem with Karmic 9.10.  It was fixed with a kernel update from a PPA.  Details are on the official report: [https://wiki.ubuntu.com/LaptopTestingTeam/AcerTimeline4810TZ](https://wiki.ubuntu.com/LaptopTestingTeam/AcerTimeline4810TZ)

My personal notes: [https://wiki.ubuntu.com/Grantbow/AcerAspire4810TZ](https://wiki.ubuntu.com/Grantbow/AcerAspire4810TZ)

---

### Post by Elif on 2010-01-11
> **grantbow said:**
> I have a 4810TZ-4696 that had an Atheros problem with Karmic 9.10.  It was fixed with a kernel update from a PPA.  Details are on the official report: [https://wiki.ubuntu.com/LaptopTestingTeam/AcerTimeline4810TZ](https://wiki.ubuntu.com/LaptopTestingTeam/AcerTimeline4810TZ)

My personal notes: [https://wiki.ubuntu.com/Grantbow/AcerAspire4810TZ](https://wiki.ubuntu.com/Grantbow/AcerAspire4810TZ)
Thanks for the help. That made most of the problem much more bearable for me on the 5810TZ. 

Still disconnecting, but much less frequently, and I can reconnect without restarting.

---

