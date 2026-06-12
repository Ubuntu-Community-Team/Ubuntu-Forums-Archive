---
title: "VIA mobo suggestion"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by chaosmedia on 2007-09-25
Hi,
I'm planning to build a small VIA based home server which will function as both a web server (LAMP) and file storage.

My plan was to use a VIA mobo and hook up two SATA drives as a mirrored RAID to run the OS (Ubuntu Server of course) and the web server stuff. For the file storage I thought I'd have some external USB/FireWire/eSATA connected 4-bay drive or something like that.

Since I'm gonna run Ubuntu server there's no X involved, so the graphics capabilities of the VIA mobos are not a priority. Looking at the VIA website there's a lot of different configurations available, and I really need some help picking the one that's best suited for my specific purpose. If anyone could help me with that I'd really appreciate it! :D

I'd like the server to be cool, silent & energy efficient, so a fanless solution would be optimal, but I know I might be asking for too much.. ;)

Thanks!

/Henrik

---

### Post by SneakyWho_am_i on 2008-03-27
Not sure how relevant this is to your proposed setup and I know it's been a couple of months but I have an issue right now where if I plug in a SATA drive, I lose my primary PATA controller.

Also the tertiary controllers meant for RAID are next to useless.

I suspect it's a driver issue more than anything else and am yet to look into it but for now it means that I'm limited to a maximum of 4 (four) disks, where in Windows I could run 10 (ten) at a time.
Same issue in Knoppix.

So before using SATA, make sure everything is going to work as you expect ;)

---

