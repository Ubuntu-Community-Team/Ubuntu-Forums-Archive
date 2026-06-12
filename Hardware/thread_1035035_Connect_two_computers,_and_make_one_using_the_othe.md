---
title: "Connect two computers, and make one using the other's processor, memory, gpu etc?"
date: 2009-01-09
forum: Hardware
---

### Post by crazyfuturamanoob on 2009-01-09
I got an older, slow, fairly useless computer, and a new, more powerful laptop.

So I want to connect these with a cable, and make this laptop using old computer's resources, how?

Here are the specs:

Acer 7520g
> 
Processor: AMD Turion 64, dual core, 2.0GHz
Graphics card: NVIDIA GeForce 8600M GS, 512Mb
RAM: 4Gb
Hard disk: 2x320Gb


Old custom crap
> 
Processor: AMD 2000 something 1.7GHz, one core
Graphics card: NVIDIA GeForce Ti 4200, 64Mb
RAM: 256Mb
Hard disk: ~70Gb


---

### Post by iggykoopa on 2009-01-09
You can look into LTSP (linux terminal server project) it's not too hard to setup and it will do what you want. Another thing you can try is turn on remote login( I think it's under the login section on admin preferences) and when you get to the login screen on the slow laptop just login remotely to the faster one.

---

### Post by surfdoc on 2009-01-09
I've done this with an old laptop (PII) and a newer desktop (Athlon XP 1.9Ghz). 

I did a normal install of Ubuntu on the newer machine and a Xubuntu install on the older one (you'll need the alternative CD for the old one because of the low memory). Then I used ssh with X tunneling to run programs on the newer machine, but displaying them on the old machine

e.g. (run this command from the old machine)

ssh -X 192.168.0.1 firefox

(where 192.168.0.1 needs to be replaced with the ip of the newer machine - note uppercase X)

Obviously your not going to want to type in a command each time, so you'll need to set up an icon for each of the common programs you use. Note that you'll need to set up "rsa keys", which will do away with entering passwords, if you want to use icons.

This works pretty well, even over a wireless network (which will be slower than your cable)

---

### Post by crazyfuturamanoob on 2009-01-09
Maybe there's a way to make it automatic, like using both computers as one computer?

Without remote login stuff or any X tunneling. And btw the laptop is the more beefy one.

---

### Post by troutbum13 on 2009-01-09
I have always wanted to play around with a beowulf cluster...might want to check it out...

---

### Post by surfdoc on 2009-01-09
Yes - I think clustering is what your looking for. Although from my limited knowledge on such things, I think you need software that is specifically written for clusters.

---

### Post by crazyfuturamanoob on 2009-01-09
So with those clusters I can get everything running faster?

---

### Post by steveneddy on 2009-01-09
> **troutbum13 said:**
> I have always wanted to play around with a beowulf cluster...might want to check it out...

I was gonna say that.

Sounds like a cluster to me.

---

### Post by btmiller on 2009-01-11
> **crazyfuturamanoob said:**
> So with those clusters I can get everything running faster?

In general, you need software written specifically to work on distributed memory systems. You might want to look at something like OpenMosix that does transparent process migration (although I seem to recall development on OpenMosiz has been somewhat inactive recently -- maybe that's changed).

---

### Post by surfdoc on 2009-01-12
OpenMosix is closed - development has moved over to LinuxPMI

---

