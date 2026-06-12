---
title: "Ubuntu Dapper Install - CD-Rom boots but doesn't mount"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by rverrips on 2006-04-05
Hi

I spent a while getting this resolved and thought best to "share" - I have an IBM NetVista Workstation (acting as proxy server) which was previously running Debian Woody happily

The HDD died so I decided to reinstall with Ubuntu Server Dapper (development release, but has proven rather stable on my Laptop workstation)

Strange thing happened during installation - The CD would boot fine, and then when after asking the questions for location, it needs to mount the CD-Rom, but fails to detect it. 

I tried to test the media, but that also wouldn't mount the CD?

So I tried my old Woody Installation CD and it worked ok - Googled a bit and discovered that there might be an issue with the IDE relating to DMA so tried the following:

Pressed F6 during installation prompt and added the following switch:
```
ide=nodma
```
Hey, worked like a charm and my Ubuntu Server is now up and running?  

Full Spec's of the Box are:

IBM NetVista 6350-G33
Pentium 4 1.8Ghz
512MB Ram
40GB HDD
CD-Rom Drive (with DMA issue)
Floppy (no issues *grin*)

---

