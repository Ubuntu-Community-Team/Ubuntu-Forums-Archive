---
title: "Packard Bell Easynote LJ61 - Cooling not working properly"
date: 2010-11-26
forum: Hardware
---

### Post by Roik93 on 2010-11-26
Hello

Today I managed to install Ubuntu Linux 10.10 x64 alongside Windows 7 x64 Pro flawlessly. I can boot both Ubuntu and Windows 7 without any issues.

However it seems that Ubuntu cannot (properly) control my CPU fan. After a while my laptop just shuts down exactly like when it overheats. This also happens when booting with the LiveCD. The only way I managed to install Ubuntu in the first place was by opening all the windows in my room to keep the CPU from overheating... I figured it might be solved after a complete install but unfortunatly not.
I don't have any heat problems in Windows 7.

Is there a way to fix this? It took me awhile to get everything set up and because Ubuntu shut down in the middle of an update, it won't boot anymore so I have to reinstall it again.

Thanks in advance

EDIT: D'oh, forgot my specs:

CPU: AMD Turion X2 64
Average CPU temperature: 63°C (idle)/up to 82°C while gaming
Motherboard: Packard Bell SJV70-PU V1.02
OS: Ubuntu Linux 10.10 x64/Windows 7 Pro x64

---

### Post by Roik93 on 2010-11-26
Shameless selfbump.

---

### Post by Roik93 on 2010-11-27
Bump. Still not resolved...

---

### Post by Roik93 on 2010-11-27
I did some more digging around and used acpi to find out some more.
acpi says the trip points are at 90*C for passive and 200°C for critical...
Could this be the problem? How do I change these settings?

I know my laptop is shutting down because of the safety measurements on my motherboard but how can I tell Ubuntu to start cooling SOONER?

---

### Post by Soldier2580 on 2010-12-13
Bump. 
I have the same laptop and I must say that I too have had this (maybe 4times in total, but sill), a solution would be nice :)

---

### Post by slgtheindividual on 2011-04-26
Bump, same laptop, same problem

---

### Post by KegHead on 2011-04-26
Hi!

Have you folks updated your kernel recently?

sudo apt-get update

sudo apt-get install linux-image -f

KegHead

---

### Post by adonet on 2013-02-26
> **KegHead said:**
> Hi!

Have you folks updated your kernel recently?

sudo apt-get update

sudo apt-get install linux-image -f

KegHead

I have updated the kernel and the fan isnt turning on. temperature is around 65C 148F while other laptops start spinning around 40C.

I am using a Packard Bell Easynote AgroC running Ubuntu 12.04.2

---

